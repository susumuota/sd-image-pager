# sd-image-pager

A minimal image viewer Desktop app for macOS, Windows and Linux.

- minimal and simple code based on [Electron Forge](https://www.electronforge.io/)
- pager-like key bindings (e.g. `space` key to move forward one page, `b` key to move backward one page)
- pre-loading images to improve performance
- macOS, Windows and Linux binaries are available

## Download

- https://github.com/susumuota/sd-image-pager/releases

## Usage

```
Key bindings (similar as 'less' command)

o, O                                       Open image files or directories.
r, R                                       Reload directories.
h, H                                       Toggle this help.
i, I                                       Toggle showing metadata as a tooltip.
q, Q                                       Quit.
f, j, PageDown, ArrowDown, Space, Enter    Move forward one page.
b, k, PageUp, ArrowUp                      Move backward one page.
g, <, Home                                 Go to first page.
G, >, End                                  Go to last page.
ArrowRight                                 Increase the number of images per page.
ArrowLeft                                  Reduce the number of images per page.
⌘+, Ctrl and +                             Zoom in.
⌘-, Ctrl and -                             Zoom out.
⌘0, Ctrl and 0                             Actual size.
F12                                        Open DevTools.
```

## Source code

- https://github.com/susumuota/sd-image-pager

## TODO

- [ ] improve app startup time (V8 snapshots?)
- [ ] watch directory change (chokidar?)

## For developers

Here's an initial log to create an Electron app with Vite, TypeScript, React and GitHub.

### Create a new Electron project with Vite and Typescript

- https://www.electronforge.io/#using-templates
- https://www.electronforge.io/templates/vite-+-typescript

```sh
node -v  # v18.17.1
yarn -v  # 1.22.19
yarn create electron-app sd-image-pager --template=vite-typescript
cd sd-image-pager
```

Test it.

```sh
yarn run start
yarn run make
open out/sd-image-pager-darwin-x64/sd-image-pager.app
```

It should be OK.

### Create a GitHub repository

Add and commit. No need to run `git init`.

```sh
git status
git add --all
git status
git commit -m "feat: initial commit."
```

Go to https://github.com/ and create a new repository `sd-image-pager`.

```sh
git remote add origin git@github.com:susumuota/sd-image-pager.git
git branch -M main
git push -u origin main
```

### Update TypeScript

TypeScript is a bit outdated so renew it.

```sh
yarn outdated
yarn add typescript@latest --dev
yarn add @typescript-eslint/eslint-plugin@latest --dev
yarn add @typescript-eslint/parser@latest --dev
yarn outdated
```

### Add React

- https://www.electronforge.io/guides/framework-integration/react-with-typescript
- https://reactjs.org/blog/2022/03/08/react-18-upgrade-guide.html#updates-to-client-rendering-apis

Install React.

```sh
yarn add react@latest react-dom@latest
yarn add @types/react @types/react-dom --dev
```

Add some template files.

- `index.html`

Add this to the inside of `body`.

```html
    <div id="app" />
```

- `src/App.tsx`

Create a new file `src/App.tsx`.

```tsx
import { createRoot } from 'react-dom/client';

function render() {
  const container = document.getElementById('app');
  if (container) {
    const root = createRoot(container);
    root.render(<h2>Hello from React!</h2>);
  }
}

render();
```

- `src/renderer.ts`

Add this to the end of the existing file.

```ts
import './App';
```

- `tsconfig.json`

Add this inside `compilerOptions`.

```json
    "jsx": "react-jsx",
```

Test it.

```sh
yarn run start
```

It should be OK.

### Choose License and create README.md

- https://choosealicense.com/

```sh
touch LICENSE     # create a file and copy license text from site. e.g. https://choosealicense.com/licenses/mit/
touch README.md   # also create a README file
```

Don't forget to change `license` field on `package.json`.

- `package.json`

```json
  "license": "MIT",
```

## License

MIT License. See [LICENSE] file.

## Author

Susumu OTA
