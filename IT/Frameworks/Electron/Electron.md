# Electron

Electron 是一个由 OpenJS Foundation 开发和维护的自由且开源的软件框架，用于使用 Web 技术创建桌面应用程序，它使用 Chromium 浏览器引擎进行渲染，并使用 Node.js 作为后端，使用此框架的著名项目有 Visual Studio Code、Atom、GitHub Desktop、QQNT 等

尽管 Electron 占用高、体积大、性能差被诟病许久，但因其跨平台体验一致、开发效率高等优点，被越来越广泛的使用

## 创建项目

**手动创建并添加依赖：**

```bash
mkdir electron-app
cd electron-app
npm init
npm install electron --save-dev
```

编写代码，然后确保 package.json 中有如下内容

```json
{
    "main": "main.js",
    "scripts": {
        "start": "electron . "
    }
}
```

运行

```bash
npm run start
```

**使用模板或工具创建：**

* [electron-react-boilerplate](https://github.com/electron-react-boilerplate/electron-react-boilerplate)
* [electron-vite](https://github.com/alex8088/electron-vite)
