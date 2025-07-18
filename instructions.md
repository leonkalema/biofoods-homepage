# BioFoods Development Instructions

## Overview
This document provides comprehensive guidelines for developing scalable, maintainable, and performant code in the BioFoods SvelteKit application. Follow these instructions to ensure code quality, consistency, and optimal performance.

## 🏗️ Architecture Principles

### Component-Based Development
- **Modular Design**: Break functionality into small, reusable components
- **Single Responsibility**: Each component should have one clear purpose
- **File Size Limit**: No file should exceed 350 lines of code
- **Composition Over Inheritance**: Prefer component composition over complex hierarchies

### Directory Structure
```
src/
├── lib/
│   ├── components/          # Reusable UI components
│   │   ├── ui/             # Basic UI elements (Button, Input, etc.)
│   │   ├── forms/          # Form-specific components
│   │   └── layout/         # Layout components
│   ├── stores/             # Svelte stores for state management
│   ├── utils/              # Utility functions and helpers
│   ├── types/              # TypeScript type definitions
│   ├── services/           # API calls and external services
│   └── constants/          # Application constants
├── routes/                 # SvelteKit routes
└── app.html               # Main HTML template
```

## 🎯 Component Development Guidelines

### Component Structure
```svelte
<script lang="ts">
  // 1. Imports (external libraries first, then internal)
  import { onMount } from 'svelte';
  import type { ComponentProps } from './types';
  
  // 2. Props with proper typing
  interface Props {
    title: string;
    items?: Item[];
    onSelect?: (item: Item) => void;
  }
  
  let { title, items = [], onSelect }: Props = $props();
  
  // 3. Local state
  let isLoading = $state(false);
  let selectedItem = $state<Item | null>(null);
  
  // 4. Derived state
  let filteredItems = $derived(items.filter(item => item.active));
  
  // 5. Functions
  function handleSelect(item: Item) {
    selectedItem = item;
    onSelect?.(item);
  }
  
  // 6. Lifecycle
  onMount(() => {
    // Initialization logic
  });
</script>

<!-- 7. Template -->
<div class="component-container">
  <!-- Component content -->
</div>

<!-- 8. Styles (if needed, prefer Tailwind) -->
<style>
  .component-container {
    /* Component-specific styles only */
  }
</style>
```

### Component Naming Conventions
- **PascalCase** for component files: `UserProfile.svelte`
- **kebab-case** for component usage: `<user-profile />`
- **Descriptive names**: `ProductCard.svelte` not `Card.svelte`
- **Prefix with domain**: `ProductCard.svelte`, `UserCard.svelte`

## 🚀 Performance Optimization

### Code Splitting & Lazy Loading
```typescript
// Use dynamic imports for route-level code splitting
const LazyComponent = lazy(() => import('./HeavyComponent.svelte'));

// Lazy load heavy utilities
const heavyUtil = await import('./utils/heavyProcessing');
```

### Svelte 5 Optimization Patterns
```svelte
<script lang="ts">
  // Use $derived for computed values
  let items = $state([]);
  let searchTerm = $state('');
  
  // Efficient derived state
  let filteredItems = $derived(
    items.filter(item => 
      item.name.toLowerCase().includes(searchTerm.toLowerCase())
    )
  );
  
  // Use $effect for side effects
  $effect(() => {
    // Only runs when dependencies change
    console.log('Items changed:', items.length);
  });
</script>
```

### Bundle Size Optimization
- **Tree Shaking**: Import only what you need
  ```typescript
  // Good
  import { debounce } from 'lodash-es/debounce';
  
  // Bad
  import _ from 'lodash';
  ```
- **Dynamic Imports**: Load components on demand
- **Image Optimization**: Use appropriate formats and sizes

## 🎨 Styling Guidelines

### Tailwind CSS Best Practices
```svelte
<!-- Use component classes for reusability -->
<div class="card">
  <h2 class="card-title">Title</h2>
  <p class="card-content">Content</p>
</div>

<style>
  .card {
    @apply bg-white rounded-lg shadow-md p-6 border border-gray-200;
  }
  
  .card-title {
    @apply text-xl font-semibold text-gray-900 mb-2;
  }
  
  .card-content {
    @apply text-gray-600 leading-relaxed;
  }
</style>
```

### Responsive Design
```svelte
<!-- Mobile-first approach -->
<div class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-3 gap-4">
  <!-- Content -->
</div>

<!-- Use container queries when available -->
<div class="@container">
  <div class="@md:flex @md:items-center">
    <!-- Content -->
  </div>
</div>
```

## 📝 TypeScript Guidelines

### Type Definitions
```typescript
// src/lib/types/index.ts
export interface User {
  id: string;
  name: string;
  email: string;
  role: 'admin' | 'user';
  createdAt: Date;
}

export interface ApiResponse<T> {
  data: T;
  message: string;
  success: boolean;
}

// Use utility types
export type UserUpdate = Partial<Pick<User, 'name' | 'email'>>;
export type UserCreate = Omit<User, 'id' | 'createdAt'>;
```

### Component Props Typing
```typescript
// Define props interface
interface ButtonProps {
  variant?: 'primary' | 'secondary' | 'danger';
  size?: 'sm' | 'md' | 'lg';
  disabled?: boolean;
  loading?: boolean;
  onclick?: () => void;
  children: Snippet;
}

let { 
  variant = 'primary', 
  size = 'md', 
  disabled = false,
  loading = false,
  onclick,
  children
}: ButtonProps = $props();
```

## 🔄 State Management

### Svelte Stores
```typescript
// src/lib/stores/user.ts
import { writable, derived } from 'svelte/store';
import type { User } from '$lib/types';

export const user = writable<User | null>(null);
export const isAuthenticated = derived(user, $user => $user !== null);

// Complex store with actions
function createUserStore() {
  const { subscribe, set, update } = writable<User | null>(null);
  
  return {
    subscribe,
    login: (userData: User) => set(userData),
    logout: () => set(null),
    updateProfile: (updates: Partial<User>) => 
      update(user => user ? { ...user, ...updates } : null)
  };
}

export const userStore = createUserStore();
```

### Context API for Component Communication
```typescript
// src/lib/context/theme.ts
import { getContext, setContext } from 'svelte';

const THEME_KEY = Symbol('theme');

export function setThemeContext(theme: 'light' | 'dark') {
  setContext(THEME_KEY, theme);
}

export function getThemeContext(): 'light' | 'dark' {
  return getContext(THEME_KEY) ?? 'light';
}
```

## 🌐 API Integration

### Service Layer Pattern
```typescript
// src/lib/services/api.ts
class ApiService {
  private baseUrl = 'https://api.biofoods.com';
  
  private async request<T>(
    endpoint: string, 
    options: RequestInit = {}
  ): Promise<ApiResponse<T>> {
    const response = await fetch(`${this.baseUrl}${endpoint}`, {
      headers: {
        'Content-Type': 'application/json',
        ...options.headers,
      },
      ...options,
    });
    
    if (!response.ok) {
      throw new Error(`API Error: ${response.statusText}`);
    }
    
    return response.json();
  }
  
  async getUsers(): Promise<User[]> {
    const response = await this.request<User[]>('/users');
    return response.data;
  }
  
  async createUser(userData: UserCreate): Promise<User> {
    const response = await this.request<User>('/users', {
      method: 'POST',
      body: JSON.stringify(userData),
    });
    return response.data;
  }
}

export const apiService = new ApiService();
```

### Error Handling
```typescript
// src/lib/utils/errorHandler.ts
export class AppError extends Error {
  constructor(
    message: string,
    public code: string,
    public statusCode: number = 500
  ) {
    super(message);
    this.name = 'AppError';
  }
}

export function handleApiError(error: unknown): AppError {
  if (error instanceof AppError) {
    return error;
  }
  
  if (error instanceof Error) {
    return new AppError(error.message, 'UNKNOWN_ERROR');
  }
  
  return new AppError('An unexpected error occurred', 'UNKNOWN_ERROR');
}
```

## 🧪 Testing Guidelines

### Component Testing
```typescript
// src/lib/components/Button.test.ts
import { render, fireEvent } from '@testing-library/svelte';
import Button from './Button.svelte';

describe('Button Component', () => {
  it('renders with correct text', () => {
    const { getByText } = render(Button, {
      props: { children: 'Click me' }
    });
    
    expect(getByText('Click me')).toBeInTheDocument();
  });
  
  it('calls onclick when clicked', async () => {
    const mockClick = vi.fn();
    const { getByRole } = render(Button, {
      props: { onclick: mockClick, children: 'Click me' }
    });
    
    await fireEvent.click(getByRole('button'));
    expect(mockClick).toHaveBeenCalledTimes(1);
  });
});
```

## 📋 Code Quality Standards

### ESLint & Prettier Configuration
- Follow the existing ESLint configuration
- Use Prettier for consistent formatting
- Run `npm run lint` before commits
- Use `npm run format` to auto-format code

### Code Review Checklist
- [ ] Component is under 350 lines
- [ ] Proper TypeScript typing
- [ ] Performance optimizations applied
- [ ] Responsive design implemented
- [ ] Error handling included
- [ ] Tests written (if applicable)
- [ ] Documentation updated

## 🚀 Deployment & Build Optimization

### Build Performance
```javascript
// vite.config.ts optimization
export default defineConfig({
  build: {
    rollupOptions: {
      output: {
        manualChunks: {
          vendor: ['svelte', '@sveltejs/kit'],
          ui: ['./src/lib/components/ui']
        }
      }
    }
  }
});
```

### Environment Configuration
```typescript
// src/lib/config/environment.ts
export const config = {
  apiUrl: import.meta.env.VITE_API_URL || 'http://localhost:3000',
  isDevelopment: import.meta.env.DEV,
  isProduction: import.meta.env.PROD,
} as const;
```

## 🔧 Development Workflow

### Git Workflow
1. Create feature branches: `feature/user-authentication`
2. Make small, focused commits
3. Write descriptive commit messages
4. Run tests before pushing
5. Create pull requests for code review

### Development Commands
```bash
# Start development server
npm run dev

# Type checking
npm run check

# Linting and formatting
npm run lint
npm run format

# Build for production
npm run build
```

## 📚 Additional Resources

### Recommended Libraries
- **Forms**: `formsnap` or `superforms`
- **Icons**: `lucide-svelte` or `heroicons`
- **Animations**: `svelte/motion` or `framer-motion`
- **Date handling**: `date-fns`
- **HTTP client**: Built-in `fetch` or `axios`

### Performance Monitoring
- Use browser DevTools for performance profiling
- Monitor bundle size with `vite-bundle-analyzer`
- Track Core Web Vitals in production

---

**Remember**: These guidelines are living documents. Update them as the project evolves and new best practices emerge. Always prioritize code readability, maintainability, and performance.
