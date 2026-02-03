# How to Update @kenneth-s/pro-components

This is a fork of `@ant-design/pro-components` published to GitHub Packages with unreleased fixes.

## Package Info

- **Package:** `@kenneth-s/pro-components`
- **Registry:** https://npm.pkg.github.com
- **Repo:** https://github.com/kenneth-s/pro-components
- **Upstream:** https://github.com/ant-design/pro-components

## Updating from Upstream

```bash
# 1. Pull latest changes from upstream
git pull origin master

# 2. Install dependencies (if lockfile changed)
pnpm install

# 3. Build the package
pnpm build

# 4. Bump version in package.json (e.g., 3.1.0-1 → 3.1.0-2)
# Edit package.json manually or use:
npm version prerelease

# 5. Publish to GitHub Packages
npm publish --ignore-scripts --access public

# 6. Push to your fork
git push kenneth-s master
```

## Using in Your Project

### 1. Configure .npmrc

```
@kenneth-s:registry=https://npm.pkg.github.com
//npm.pkg.github.com/:_authToken=${GITHUB_TOKEN}
```

### 2. Set GITHUB_TOKEN

```bash
export GITHUB_TOKEN=$(gh auth token)
```

Or add to your shell profile (~/.zshrc, ~/.bashrc).

### 3. Add to package.json

```json
{
  "dependencies": {
    "@ant-design/pro-components": "npm:@kenneth-s/pro-components@3.1.0-1"
  }
}
```

This aliases the package so your imports stay unchanged:

```tsx
import { ProTable, ProForm } from '@ant-design/pro-components';
```

### 4. Install

```bash
pnpm install
```

## CI/CD

In GitHub Actions, use the built-in `GITHUB_TOKEN`:

```yaml
- name: Install dependencies
  run: pnpm install
  env:
    GITHUB_TOKEN: ${{ secrets.GITHUB_TOKEN }}
```

## Reverting to Official npm Package

Remove the alias and install the official version:

```json
{
  "dependencies": {
    "@ant-design/pro-components": "^2.8.10"
  }
}
```
