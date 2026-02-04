# ResoniteLink.js Bug Report Reproduction

This repository was created to report [xhayper/ResoniteLink.js#1](https://github.com/xhayper/ResoniteLink.js/issues/1).

This repository reproduces a circular dependency issue found in [ResoniteLink.js](https://github.com/xhayper/ResoniteLink.js).

## Issue

### Circular dependency error when importing the library

When importing the built library, a circular dependency causes `Base` class to be undefined:

```
TypeError: Class extends value undefined is not a constructor or null
    at Object.<anonymous> (.../dist/client/managers/baseManager.js:5:36)
```

## Reproduction Steps

### Prerequisites

- Node.js v20+
- npm

### Setup

```bash
# Clone with submodule
git clone --recurse-submodules <this-repo>
cd test-ResoniteLink.js

# Install dependencies
npm install

# Build the submodule
cd ResoniteLink.js
npm install
npm run build
cd ..
```

### Reproduce

```bash
npx tsx index.ts
```

**Result:**
```
TypeError: Class extends value undefined is not a constructor or null
```

## Environment

- Node.js: v20.14.0
- OS: Windows 11
- ResoniteLink.js: v0.0.0-alpha.0

## Files

- `index.ts` - README example code (unchanged)
- `ResoniteLink.js/` - Git submodule of the library
