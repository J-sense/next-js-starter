# Next.js Starter Template

A modern, feature-rich Next.js starter template with TypeScript, Tailwind CSS, shadcn/ui components, and a pre-built dashboard layout.

## 🚀 Features

- **Next.js 16** - Latest version with App Router
- **React 19** - Modern React with latest features
- **TypeScript** - Full type safety and better IDE support
- **Tailwind CSS 4** - Utility-first CSS framework
- **shadcn/ui** - High-quality, accessible React components
- **ESLint** - Code quality and consistency
- **Dashboard Layout** - Pre-configured multi-layout structure
  - Common layout for public pages
  - Dashboard layout with sidebar for admin/user areas
- **Responsive Sidebar** - Mobile-friendly navigation component
- **Icon Library** - Lucide React icons for rich UI
- **Utility Helpers** - Reusable utility functions for styling
- **Mobile Support** - Custom hook for detecting mobile devices

## 📋 Project Structure

```
next_starter/
├── app/                          # Next.js app directory
│   ├── globals.css              # Global styles
│   ├── layout.tsx               # Root layout
│   ├── (commonLayout)/          # Public pages layout group
│   │   ├── layout.tsx
│   │   └── page.tsx
│   └── (dashboardLayout)/       # Dashboard layout group
│       ├── layout.tsx
│       ├── admin/
│       │   └── page.tsx
│       └── user/
│           └── page.tsx
├── components/
│   ├── ui/                      # Reusable UI components
│   │   ├── avatar.tsx
│   │   ├── breadcrumb.tsx
│   │   ├── button.tsx
│   │   ├── collapsible.tsx
│   │   ├── dropdown-menu.tsx
│   │   ├── input.tsx
│   │   ├── separator.tsx
│   │   ├── sheet.tsx
│   │   ├── sidebar.tsx
│   │   ├── skeleton.tsx
│   │   └── tooltip.tsx
├── src/
│   └── components/
│       └── sidebar/              # Dashboard sidebar components
│           ├── app-sidebar.tsx
│           ├── nav-main.tsx
│           ├── nav-projects.tsx
│           ├── nav-user.tsx
│           └── team-switcher.tsx
├── hooks/
│   └── use-mobile.ts            # Mobile detection hook
├── lib/
│   └── utils.ts                 # Utility functions
├── public/                       # Static assets
├── package.json
├── tsconfig.json
├── next.config.ts
├── postcss.config.mjs
├── eslint.config.mjs
└── components.json
```

## 🛠️ Tech Stack

### Core Dependencies

- **next** - React framework for production
- **react** - UI library
- **react-dom** - DOM rendering
- **typescript** - Type safety

### UI & Styling

- **@tailwindcss/postcss** - CSS framework
- **tailwindcss** - Utility-first CSS
- **class-variance-authority** - Variant management
- **clsx** - Conditional classnames
- **tailwind-merge** - Merge Tailwind classes
- **tw-animate-css** - Tailwind animation utilities

### Components & Icons

- **@radix-ui/** - Accessible component primitives
  - react-avatar
  - react-collapsible
  - react-dialog
  - react-dropdown-menu
  - react-separator
  - react-slot
  - react-tooltip
- **lucide-react** - Beautiful icon library

### Development Tools

- **eslint** - Code linting
- **eslint-config-next** - Next.js ESLint config
- **@types/react** - React type definitions
- **@types/react-dom** - React DOM type definitions
- **@types/node** - Node.js type definitions

## 🚀 Getting Started

### Prerequisites

- Node.js 18+
- npm or yarn

### Installation

1. Clone the repository:

```bash
git clone <repository-url>
cd next_starter
```

2. Install dependencies:

```bash
npm install
```

3. Run the development server:

```bash
npm run dev
```

4. Open [http://localhost:3000](http://localhost:3000) in your browser to see the result.

## 📝 Available Scripts

- `npm run dev` - Start the development server
- `npm run build` - Build the project for production
- `npm start` - Start the production server
- `npm run lint` - Run ESLint to check code quality

## 🏗️ Architecture

### Layout Groups

This template uses Next.js layout groups to organize different page layouts:

**Common Layout** (`(commonLayout)`)

- Used for public-facing pages
- Basic layout without sidebar
- Ideal for landing pages, documentation, etc.

**Dashboard Layout** (`(dashboardLayout)`)

- Used for authenticated/admin pages
- Includes sidebar navigation
- Separate routes for admin (`/admin`) and user (`/user`) areas

### Component Organization

- **UI Components** (`components/ui/`) - Shadcn/ui components with Tailwind styling
- **Feature Components** (`src/components/`) - Application-specific components like sidebar navigation
- **Hooks** (`hooks/`) - Custom React hooks (e.g., mobile detection)
- **Utilities** (`lib/utils.ts`) - Helper functions for class merging and styling

## 🎨 Styling

### Tailwind CSS Configuration

The project uses Tailwind CSS with:

- New York style from shadcn/ui
- CSS variables for theming
- Neutral base color
- Full responsive utilities

### Adding New Components

To add new shadcn/ui components:

```bash
npx shadcn-ui@latest add <component-name>
```

## 📱 Responsive Design

The `use-mobile` hook helps detect mobile devices:

```tsx
import { useIsMobile } from "@/hooks/use-mobile";

export function MyComponent() {
  const isMobile = useIsMobile();

  return isMobile ? <MobileView /> : <DesktopView />;
}
```

## 🔗 Path Aliases

Configured path aliases for cleaner imports:

```
@/ → Root directory
@/components → components/
@/ui → components/ui/
@/lib → lib/
@/hooks → hooks/
```

## 🚀 Deployment

### Vercel (Recommended)

1. Push your code to GitHub, GitLab, or Bitbucket
2. Go to [vercel.com](https://vercel.com)
3. Import your repository
4. Deploy automatically

### Docker

Create a `Dockerfile`:

```dockerfile
FROM node:18-alpine AS base

FROM base AS deps
WORKDIR /app
COPY package.json package-lock.json ./
RUN npm ci

FROM base AS builder
WORKDIR /app
COPY package.json package-lock.json ./
RUN npm ci
COPY . .
RUN npm run build

FROM base AS runner
WORKDIR /app
RUN addgroup -g 1001 -S nodejs
RUN adduser -S nextjs -u 1001
COPY --from=builder /app/.next/standalone ./
COPY --from=builder /app/.next/static ./.next/static
USER nextjs
EXPOSE 3000
CMD ["node", "server.js"]
```

## 📖 Next.js Resources

- [Next.js Documentation](https://nextjs.org/docs)
- [Next.js App Router](https://nextjs.org/docs/app)
- [Tailwind CSS Documentation](https://tailwindcss.com/docs)
- [shadcn/ui Components](https://ui.shadcn.com)
- [Radix UI Documentation](https://www.radix-ui.com)

## 🤝 Contributing

1. Create a feature branch (`git checkout -b feature/amazing-feature`)
2. Commit your changes (`git commit -m 'Add amazing feature'`)
3. Push to the branch (`git push origin feature/amazing-feature`)
4. Open a Pull Request

## 📄 License

This project is open source and available under the MIT License.

## 🆘 Troubleshooting

### Port 3000 Already in Use

Change the port:

```bash
npm run dev -- -p 3001
```

### Build Errors

Clear the cache and reinstall:

```bash
rm -rf .next node_modules package-lock.json
npm install
npm run build
```

### TypeScript Errors

Regenerate type definitions:

```bash
npm run dev
```

## 💡 Tips & Best Practices

1. **Component Structure** - Keep components small and focused
2. **Type Safety** - Always define prop types with TypeScript interfaces
3. **Performance** - Use `use client` directive only when necessary
4. **Styling** - Leverage Tailwind CSS utilities before adding custom CSS
5. **Icons** - Use Lucide React icons from `lucide-react`
6. **Reusability** - Extract components to `components/ui/` for reuse

---

**Happy coding! 🎉**
