# Portfolio Landing Page Deployment Procedure

## Quick Start
1. Clone repository
2. Install dependencies
3. Copy existing component
4. Configure Next.js
5. Deploy

## Detailed Steps

### 1. Project Setup
```bash
# Create new Next.js project
npx create-next-app@latest portfolio-landing --typescript --tailwind --eslint
cd portfolio-landing

# Install dependencies
npm install lucide-react
npm install class-variance-authority clsx tailwind-merge
```

### 2. Component Integration
1. Copy the existing PortfolioPage.tsx to src/components/
2. Create pages/index.tsx to import and use the component
3. Update component imports to use shadcn/ui

### 3. Configuration
```typescript
// pages/index.tsx
import PortfolioPage from '../components/PortfolioPage'

export default function Home() {
  return <PortfolioPage />
}
```

### 4. Build & Deploy
```bash
# Build project
npm run build

# Test locally
npm run dev

# Deploy
npm run build
npm run start
```

### 5. Verification Checklist
- [ ] All components render correctly
- [ ] Responsive design works
- [ ] Navigation functions properly
- [ ] No console errors
- [ ] Performance is optimized

## Troubleshooting
1. Module not found errors
   - Check dependencies
   - Verify import paths
2. Styling issues
   - Confirm Tailwind config
   - Check shadcn/ui setup

## Notes
- Keep node_modules up to date
- Test locally before deployment
- Maintain backup of configuration