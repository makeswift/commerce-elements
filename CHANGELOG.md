# commerce-elements

## 0.2.0

### Minor Changes

- **BREAKING**: Switched from shipping source files to compiled JavaScript
- Package now ships pre-built ESM and CommonJS bundles
- No longer requires `transpilePackages` configuration in Next.js
- Works out of the box with all frameworks (Next.js, Vite, Remix, etc.)
- Added `prepublishOnly` script to ensure package is built before publishing

### What This Means for Users

- **Upgrade**: Just run `npm install commerce-elements@latest`
- **Remove**: The `transpilePackages: ['commerce-elements']` line from `next.config.js` (no longer needed!)
- Everything else stays the same

## 0.1.2

### Patch Changes

- Fixed module resolution for Next.js by adding explicit .tsx file extensions to imports
- Updated README with correct CSS import order (must come before @tailwind directives)

## 0.1.1

### Patch Changes

- Fixed CSS export to exclude Tailwind directives (prevents duplicate @tailwind imports)
- Created separate styles.css for user imports (CSS variables only)
- Updated documentation with correct Tailwind CSS setup instructions
- Improved customization examples in README

## 0.1.0

### Minor Changes

- Initial release
- Button component with multiple variants (primary, secondary, tertiary, ghost, danger)
- Button sizes (large, medium, small, x-small)
- Button shapes (pill, rounded, square, circle)
- Loading state support
- Tailwind CSS preset with custom design tokens
- CSS variables for easy theming
- TypeScript support
- Full accessibility support
