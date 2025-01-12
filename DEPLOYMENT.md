# Portfolio Landing Page Deployment Procedure

## Overview
Step-by-step guide for deploying the portfolio landing page.

## Steps

### 1. Setup
```bash
git clone https://github.com/[username]/portfolio-landing
cd portfolio-landing
npx create-next-app@latest . --typescript --tailwind --eslint
```

### 2. Install Dependencies
```bash
npm install lucide-react class-variance-authority clsx tailwind-merge
```

### 3. Project Structure
```
src/
  components/
    PortfolioPage.tsx
  pages/
    index.tsx
```

### 4. Configuration
Update tailwind.config.js and tsconfig.json as needed.

### 5. Deploy
```bash
npm run build
npm run start
git push origin main
```

### 6. Verify
1. Check deployment status
2. Test functionality
3. Verify components

## Resources
- Next.js docs: nextjs.org/docs
- Tailwind: tailwindcss.com