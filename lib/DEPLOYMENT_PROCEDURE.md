# Portfolio Landing Page Deployment Procedure

## Project Overview
This document outlines the step-by-step procedure for deploying the portfolio landing page as a Next.js application.

## Prerequisites
- Node.js (v16 or later)
- Git
- GitHub account
- Basic knowledge of Next.js and React

## Step 1: Repository Setup
```bash
# Clone the repository
git clone https://github.com/[username]/portfolio-landing
cd portfolio-landing

# Initialize a new Next.js project
npx create-next-app@latest . --typescript --tailwind --eslint
```

## Step 2: Dependencies Installation
```bash
# Install required dependencies
npm install @/components/ui/card @/components/ui/button @/components/ui/tabs @/components/ui/badge
npm install lucide-react
npm install class-variance-authority clsx tailwind-merge
```

## Step 3: Project Structure
Ensure the following structure:
```
portfolio-landing/
├── src/
│   ├── components/
│   │   └── PortfolioPage.tsx    # Main component
│   ├── pages/
│   │   └── index.tsx            # Entry point
│   └── styles/
│       └── globals.css          # Global styles
├── public/
├── package.json
└── tsconfig.json
```

## Step 4: Component Integration
1. Copy the existing PortfolioPage component to `src/components/`
2. Update imports to use correct paths
3. Ensure all shadcn/ui components are properly imported

## Step 5: Configuration Files
### tailwind.config.js
```javascript
module.exports = {
  content: [
    './src/pages/**/*.{js,ts,jsx,tsx}',
    './src/components/**/*.{js,ts,jsx,tsx}',
  ],
  theme: {
    extend: {},
  },
  plugins: [],
}
```

### tsconfig.json
```json
{
  "compilerOptions": {
    "baseUrl": ".",
    "paths": {
      "@/*": ["./src/*"]
    }
  }
}
```

## Step 6: GitHub Actions Setup
Create `.github/workflows/deploy.yml`:
```yaml
name: Deploy Portfolio

on:
  push:
    branches: [ main ]

jobs:
  deploy:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v2
      - uses: actions/setup-node@v2
        with:
          node-version: '16'
      - run: npm ci
      - run: npm run build
      - run: npm run export
```

## Step 7: Deployment
```bash
# Build the project
npm run build

# Test locally
npm run start

# Deploy
git add .
git commit -m "Initial deployment"
git push origin main
```

## Step 8: Verification
1. Check GitHub Actions for successful deployment
2. Verify the live site at the deployed URL
3. Test responsiveness and functionality
4. Verify all components are rendering correctly

## Troubleshooting
Common issues and solutions:

1. **Module not found errors**
   - Verify all dependencies are installed
   - Check import paths are correct
   - Ensure tsconfig.json paths are properly configured

2. **Styling issues**
   - Confirm Tailwind is properly configured
   - Check for any arbitrary value usage in classes
   - Verify shadcn/ui component styles are imported

3. **Build failures**
   - Check for TypeScript errors
   - Verify all required dependencies are listed in package.json
   - Ensure no usage of browser-only APIs in SSR code

## Maintenance
- Regularly update dependencies
- Monitor GitHub Actions for any deployment issues
- Keep documentation updated with any changes
- Backup your deployment configuration

## Additional Resources
- Next.js Documentation: https://nextjs.org/docs
- Tailwind CSS Documentation: https://tailwindcss.com/docs
- shadcn/ui Documentation: https://ui.shadcn.com/docs

## Notes
- Always test locally before deploying
- Keep track of any environment variables needed
- Maintain a development branch for testing new features
- Regular backups of configuration files recommended