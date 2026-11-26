# smrt-desktop consumer fixture

A throwaway application used to prove that a repository outside
[happyvertical/smrt](https://github.com/happyvertical/smrt) can build an
unsigned desktop bundle with the published `@happyvertical/smrt-desktop`
package (smrt#4965). It is not a product: the bundle identifier is an
`invalid.example` placeholder and the icons are the wrapper's placeholders.

Scaffolded from `@happyvertical/smrt-template-sveltekit` 0.72.0, plus
`smrt-desktop.json`, the owner-link route and `desktop/smrt-mcp-bridge.mjs`.
The bridge is a generated file, committed because no published package ships a
pre-bundled one yet:

```sh
esbuild node_modules/@happyvertical/smrt-app-cli/dist/bin/smrt-mcp-bridge.js \
  --bundle --platform=node --format=esm --target=node24 \
  --outfile=desktop/smrt-mcp-bridge.mjs \
  --banner:js='import { createRequire as __smrtCreateRequire } from "node:module"; const require = __smrtCreateRequire(import.meta.url);'
```
