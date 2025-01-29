## Overview

This is a demo Node.js project to replicate the issue found in Renovate.

### Problem

Renovate updates `package-lock.json` file for the `npm` transitive **dev** dependency by moving it under `dependencies` and dropping `"dev": true` flag.

```diff
{
  "packages": {
    "": {
+    "dependencies": {
+       "npm": "^10.9.2"
+     },
      "devDependencies": {
        "@semantic-release/npm": "^12.0.0"
      },
      // ...
    },
    "node_modules/npm": {
+     "version": "10.9.2",
-     "dev": true,
      // ...
    },
    // ...
  }
}
```

Related Discussion: [renovatebot/renovate#33745](https://github.com/renovatebot/renovate/discussions/33745).
