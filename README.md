# electron-react-starter

A starter for desktop apps with Electron, React, TypeScript and Tailwind CSS v4, built with webpack. Nothing here comes from a template generator. It's two webpack configs plus electron-builder for packaging.

I wrote up every file and why it's there in [How to set up Electron with React, TypeScript and webpack](https://www.hassandev.me/blog/youtube/creating-an-electronreact-dev-environment-with-webpack-QtxvjvhhIak), and the page has the video where I build it from scratch.

## Use it

```bash
git clone https://github.com/hassanaziz0012/electron-react-starter.git
cd electron-react-starter
npm install
npm run dev
```

The first `npm run dev` downloads the Electron binary, so give it a minute. Then a window opens with the React app. Edits to the React code show up straight away, and edits to `src/main.ts` restart the app. Stop it with Ctrl+C.

| Script | What it does |
|---|---|
| `npm run dev` | React dev server on port 3000, webpack watching the main process, and Electron through electronmon |
| `npm run build` | Production build of both processes into `dist` |
| `npm run package` | Build, then package an installer into `build` with electron-builder (NSIS on Windows, DMG on macOS, AppImage on Linux) |

Change `appId` and `productName` in the `build` block of `package.json`, and the `<title>` in `public/index.html`, before you ship your own app.

## Layout

- `src/main.ts` is the Electron main process. It loads `localhost:3000` in development and `dist/renderer/index.html` in production.
- `src/renderer.tsx` mounts the React app from `src/App.tsx`.
- `src/styles/global.css` is the Tailwind entry point.
- `webpack/webpack.main.js` and `webpack/webpack.renderer.js` build the two processes.

## Notes

- TypeScript is pinned to 6. ts-loader needs the TypeScript compiler API, and the TypeScript 7 package doesn't ship one.
- On Windows, electron-builder needs Visual Studio with its build tools, and the first `npm run package` has to run from an administrator terminal.
- Tested on Linux with Electron 44.7 and 45.0.
