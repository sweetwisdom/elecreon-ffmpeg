# electron-ffmpeg (super transcoding)

![image-20220412121741509](https://s2.loli.net/2022/04/12/HFYVUe1vKmnp2rC.png)

่ฏญ่จ:[ไธญๆ](./README-zh.md)

> technology stack: vue3 + vite + electron + elementui + ffmpeg
>
> project templates: ๐ฅณ ++ integrated templates -- **simple in structure and easy to get started!** ` Electron``Vue3``Vite2 `

Special thanks here to [caoxiemeihao ]([electron-vite/electron-vite-boilerplate: Electron + Vite + TypeScript. Support SerialPort, SQLite3 and node C/C++ addons. (github.com)](https://github.com/electron-vite/electron-vite-boilerplate))

## function

video and audio format conversion

input format = ["mp4", "flv", "ts", "mkv", "avi", "wmv"]

output format = ["mp4", "flv", "ts", "mkv", "avi", "wmv", 'mp3']

> note: the wmv format is too slow to be used

**use effects**

![Honeycam 2022-04-12 12-29-07](https://s2.loli.net/2022/04/12/Oz1cML4rpV9Xg6U.gif)

## project initialization

### required configuration

- Node `version ">=16.0.0"`
- npm package management tool, recommended`yarn`
- global installation electron (used in project development)

if the node version is not good, it is recommended to use nvm to manage multiple versions. refer to [the latest configuration tutorial for nvm 2022 - zhihu (zhihu.com](https://zhuanlan.zhihu.com/p/474109586)).

![image-20220412114106710](.imgs/image-20220412114106710.png)

install yarn, electron

```shell
 npm config set ELECTRON_MIRROR http://npm.taobao.org/mirrors/electron/
 # ่ฎพ็ฝฎelectron ไธบๅฝๅ้ๅ
npm i yarn -g
yarn global  add electron
# ่ฟๅฅ้กน็ฎ  ๅฎ่ฃไพ่ต
yarn install
```

### launch & package

![image-20220412122100314](.imgs/image-20220412122100314.png)

```shell
# dev
yarn dev

# build

yarn build
```

## directory structure

```tree
electron-vue3

โโโ dist
โ   โโโ main
โ   โ   โโโ index.cjs
โ   โ   โโโ package.js
โ   โโโ preload
โ       โโโ index.cjs
โโโ public
โ   โโโ package.json
โ   โโโ super.ico
โ   โโโ tool.exe  # ffmpeg
โ   โโโ yarn.lock   # nodemodule for packge
โ
โโโ configs
โ   โโโ vite-main.config.ts          Main process configuration file, compile SRC /main
โ   โโโ vite-preload.config.ts       Preloads the script configuration file and compiles SRC /preload
โ   โโโ vite-renderer.config.ts      Renderer configuration file, compile SRC /renderer
โ
โโโ scripts
โ   โโโ build.mjs                    Project build script, corresponding to NPM Run Build
โ   โโโ electron-builder.config.mjs
โ   โโโ watch.mjs                    Project development script, corresponding to NPM run dev
โ
โโโ src
โ   โโโ main                         Main process source code
โ   โโโ preload                      Preload the script source code
โ   โโโ renderer                     Render process source code
โ
```

#### `dist` and `src`

- once the script has been started or packaged, a **`dist` folder is created in the root directory, which is exactly the same as `src`**
- when using some path calculations, especially relative path calculations; maintaining the same directory structure as inside can avoid many problems` dist``src `

```tree
โโโ dist
โ   โโโ main
โ   โโโ preload
โ   โโโ renderer
โโโ src
โ   โโโ main
โ   โโโ preload
โ   โโโ renderer
โ
```
