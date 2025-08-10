# Vue

Vue 是一个开源的 MVVM (Model-View-ViewModel) 前端 JavaScript 框架，用于构建用户界面和单页应用程序

## 创建项目

```bash
npm create vue@latest
cd your-project-name
npm install
npm run dev
```

## 创建应用

推荐使用 vite 创建

```bash
npm create vite@latest
cd your-project-name
npm install
npm run dev
```

## 单文件组件

一般将 Vue 组件定义在一个单独的 `.vue` 文件中，这被称为单文件组件（SFC, Single File Component）

## 模板语法

## Typescript

### `lang="ts"`

在 `<script>` 或 `<script setup>` 标签上加上 `lang="ts"` 属性启用 Typescript

```html
<script setup lang="ts">
    // ...
</script>
```

### `ref()`

`ref()` 会根据初始化值推导类型，也可显式声明类型。若未给出初始值，则会得到一个包含 `undefined` 的联合类型

```ts
const ciallo = ref('0721'); // Ref<string>
const aaa: Ref<string | number> = ref(114514);
const homo = ref<string | number>(1919810);
const x = ref<number>(); // Ref<number | undefined>
```
