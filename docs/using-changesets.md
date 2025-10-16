# Using Changesets

Changesets is set up to help you manage versions and changelogs automatically!

## Workflow

### 1. Make Your Changes

Work on your feature/fix as normal:

```bash
# Create a new component, fix a bug, etc.
git checkout -b feature/new-select-component
# ... make your changes ...
```

### 2. Create a Changeset

When you're done, describe what changed:

```bash
pnpm changeset
```

This will prompt you:

```
🦋  Which packages would you like to include?
› ◉ commerce-elements

🦋  What kind of change is this for commerce-elements?
  ○ major (breaking change)
  ○ minor (new feature)
  ● patch (bug fix)

🦋  Please enter a summary for this change:
│ Added new Select component with keyboard navigation support
```

This creates a file in `.changeset/` describing your change.

### 3. Commit Everything

```bash
git add .
git commit -m "Add Select component"
git push
```

**Important:** Commit the changeset file along with your code!

### 4. When Ready to Release

Run the version command to consume all changesets:

```bash
pnpm version
```

This will:

- ✅ Update `package.json` version
- ✅ Generate/update `CHANGELOG.md`
- ✅ Delete the changeset files (they're consumed)
- ✅ Create a commit with all changes

### 5. Publish

```bash
# Review the changes
git log -p

# Publish to npm
pnpm release
```

This publishes to npm and creates a git tag.

### 6. Push Everything

```bash
git push --follow-tags
```

## Examples

### Bug Fix (Patch: 0.1.0 → 0.1.1)

```bash
pnpm changeset
# Select: patch
# Summary: "Fixed Button focus ring on Safari"
```

### New Feature (Minor: 0.1.0 → 0.2.0)

```bash
pnpm changeset
# Select: minor
# Summary: "Added new Select component with full accessibility support"
```

### Breaking Change (Major: 0.1.0 → 1.0.0)

```bash
pnpm changeset
# Select: major
# Summary: "Renamed Button 'variant' prop to 'color' for consistency"
```

## Multiple Changes at Once

You can create multiple changesets before releasing:

```bash
# Fix a bug
pnpm changeset
# > patch: "Fixed Button disabled state"

# Add a feature
pnpm changeset
# > minor: "Added Input component"

# Add another feature
pnpm changeset
# > minor: "Added Card component"

# When ready, bundle them all into one release
pnpm version  # Creates v0.2.0 with all changes in the changelog
pnpm release
```

## The Generated CHANGELOG

Changesets will automatically create/update `CHANGELOG.md`:

```md
# commerce-elements

## 0.2.0

### Minor Changes

- a1b2c3d: Added Input component with validation
- d4e5f6g: Added Card component with variants

### Patch Changes

- h7i8j9k: Fixed Button disabled state on mobile

## 0.1.0

### Minor Changes

- Initial release with Button component
```

## Advanced: Detailed Changesets

You can write more detailed changesets by editing the generated `.md` files:

```bash
pnpm changeset
# Creates .changeset/brave-wolves-dance.md
```

Edit the file for more detail:

```md
---
'commerce-elements': minor
---

Added new Select component

This component includes:

- Full keyboard navigation
- Screen reader support
- Multi-select mode
- Custom styling via CSS variables

Breaking changes:

- None

Migration guide:

- Simply import and use: `import { Select } from 'commerce-elements'`
```

## Tips

1. **One changeset per PR/feature** - Makes it easy to track what changed
2. **Be descriptive** - The summary goes into the changelog
3. **Version before you forget** - Run `pnpm version` regularly
4. **Use semantic versioning correctly**:
   - **Patch**: Bug fixes only
   - **Minor**: New features, backward compatible
   - **Major**: Breaking changes

## Automation (Optional)

You can set up GitHub Actions to automate this:

```yaml
# .github/workflows/release.yml
name: Release

on:
  push:
    branches:
      - main

jobs:
  release:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v3
      - uses: pnpm/action-setup@v2
      - uses: actions/setup-node@v3
      - run: pnpm install
      - run: pnpm changeset version
      - run: pnpm changeset publish
        env:
          NPM_TOKEN: ${{ secrets.NPM_TOKEN }}
```

This will automatically publish when you merge changesets to main!

For now, manual releases give you full control and are perfectly fine.
