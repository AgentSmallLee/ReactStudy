# React 小白学习路线（从零开始）

> 适用人群：完全没有 React 基础，有一定 HTML/CSS/JS 基础的前端初学者
> 学习目标：掌握 React 核心概念，为学习 React Native 打下基础
> 建议学习周期：4-6 周（每天 1-2 小时）

---

## 前置知识检查

在开始学 React 之前，确保你已经掌握以下 JavaScript 知识：

| 知识点 | 重要程度 | 说明 |
|--------|---------|------|
| 变量（let/const）、数据类型 | ⭐⭐⭐⭐⭐ | 基础中的基础 |
| 函数、箭头函数 | ⭐⭐⭐⭐⭐ | React 中大量使用 |
| 数组方法（map、filter、reduce） | ⭐⭐⭐⭐⭐ | 列表渲染必须会 |
| 对象、解构赋值 | ⭐⭐⭐⭐⭐ | props 和 state 经常用 |
| 模板字符串 | ⭐⭐⭐⭐ | 字符串拼接 |
| 展开运算符（...） | ⭐⭐⭐⭐⭐ | state 更新常用 |
| Promise、async/await | ⭐⭐⭐⭐ | 网络请求需要 |
| ES6 模块（import/export） | ⭐⭐⭐⭐⭐ | 组件化必须 |
| 三元表达式、短路与（&&） | ⭐⭐⭐⭐ | 条件渲染常用 |

> 如果上面有不熟悉的，先花 2-3 天补一下 JavaScript 基础，再开始学 React。

---

## 🗺️ 学习路线总览

```
第 1 阶段：React 基础概念（1 周）
    ↓
第 2 阶段：Hooks 与状态管理（1 周）
    ↓
第 3 阶段：组件设计与通信（1 周）
    ↓
第 4 阶段：路由与数据请求（1 周）
    ↓
第 5 阶段：状态管理库与进阶（1-2 周）
```

---

## 第一阶段：React 基础概念（1 周）

### 学习目标

- 理解 React 是什么，能写第一个 React 组件
- 理解 JSX、Props、State 的概念

### 学习内容

#### 1.1 React 介绍与环境

| 知识点 | 说明 |
|--------|------|
| **React 是什么** | 一个用于构建用户界面的 JavaScript 库 |
| **为什么用 React** | 组件化、声明式、虚拟 DOM、跨平台 |
| **创建项目** | `npm create vite@latest my-app -- --template react-ts` |

> 用 Vite + TypeScript 创建项目，和 React Native 的技术栈最接近。

#### 1.2 JSX 语法（必须熟练掌握）

JSX 是 JavaScript 和 HTML 的混合写法，React 组件的核心。

```jsx
// JSX 看起来像 HTML，但其实是 JavaScript
function Welcome() {
  const name = "小明";
  return <h1>Hello, {name}!</h1>;
}
```

| 知识点 | 说明 | 示例 |
|--------|------|------|
| **基本写法** | 用 JSX 描述 UI | `<div>Hello</div>` |
| **表达式嵌入** | 用 `{}` 写 JS 表达式 | `<h1>Hello, {name}</h1>` |
| **className** | 用 className 代替 class | `<div className="box">` |
| **style** | 样式用对象写法 | `<div style={{ color: 'red' }}>` |
| **条件渲染** | 三元、&&、\|\| | `{isLogin && <UserInfo />}` |
| **列表渲染** | map + key | `list.map(item => <li key={item.id}>{item.name}</li>)` |
| **事件绑定** | onClick、onChange 等 | `<button onClick={handleClick}>` |
| **Fragment** | 空标签，不额外生成 DOM | `<>` 或 `<React.Fragment>` |

#### 1.3 组件基础

| 概念 | 说明 |
|------|------|
| **函数组件** | 用函数定义组件（React 推荐写法） |
| **组件名大写** | 组件名必须以大写字母开头 |
| **组件嵌套** | 组件可以像 HTML 标签一样互相嵌套 |
| **Props** | 父组件传给子组件的数据，只读 |
| **默认 Props** | 给 props 设置默认值 |

### 动手练习

- [ ] 用 Vite 创建一个 React + TypeScript 项目并跑起来
- [ ] 写一个 `HelloWorld` 组件，显示你的名字
- [ ] 写一个 `UserCard` 组件，接收 name、age、avatar 三个 props
- [ ] 用 `map` 渲染一个学生列表（数组里有 5 个学生对象）
- [ ] 实现一个简单的条件渲染：登录显示用户名，未登录显示登录按钮

### 常见困惑

> **Q: JSX 里的 `{}` 是什么？**
> A: 在 JSX 里用大括号包裹 JavaScript 表达式，可以放变量、函数调用、运算等。

> **Q: 为什么要用 `className` 而不是 `class`？**
> A: 因为 `class` 是 JavaScript 的保留字，所以 React 用 `className` 代替。

> **Q: 为什么列表渲染要加 `key`？**
> A: 帮助 React 识别哪些元素改变了，提高渲染性能。key 必须是唯一的。

---

## 第二阶段：Hooks 与状态管理（1 周）⭐ 最核心

### 学习目标

- 掌握 useState 和 useEffect 这两个最重要的 Hook
- 理解 React 的状态更新机制

### 学习内容

#### 2.1 useState（状态钩子）

最基础最重要的 Hook，用于在函数组件中添加状态。

```jsx
const [count, setCount] = useState(0);
// count 是状态值，setCount 是更新函数，0 是初始值
```

| 知识点 | 说明 |
|--------|------|
| **基本用法** | `const [state, setState] = useState(initialValue)` |
| **状态不可变** | 不能直接改 state，必须用 setState |
| **对象/数组更新** | 用展开运算符 `...` 创建新的对象/数组 |
| **函数式更新** | 新状态依赖旧状态时用：`setCount(prev => prev + 1)` |
| **惰性初始化** | 初始值是计算结果时用函数：`useState(() => computeInitial())` |

#### 2.2 useEffect（副作用钩子）

第二个最重要的 Hook，用于处理副作用（数据请求、订阅、DOM 操作等）。

```jsx
// 每次渲染后执行
useEffect(() => {
  console.log('组件渲染了');
});

// 只在挂载时执行一次（空依赖数组）
useEffect(() => {
  fetchData();
}, []);

// 依赖变化时执行
useEffect(() => {
  // count 变化时执行
}, [count]);

// 清理函数
useEffect(() => {
  const timer = setInterval(...);
  return () => clearInterval(timer); // 组件卸载时清理
}, []);
```

| 知识点 | 说明 |
|--------|------|
| **基本用法** | `useEffect(callback, dependencies)` |
| **依赖数组** | 控制 effect 什么时候执行 |
| **空依赖数组 `[]`** | 只在组件挂载时执行一次 |
| **清理函数** | return 一个函数，在卸载/下一次 effect 前执行 |
| **常见用途** | 数据请求、定时器、事件监听、订阅 |

#### 2.3 其他常用 Hooks

| Hook | 用途 | 重要程度 |
|------|------|---------|
| `useState` | 组件状态 | ⭐⭐⭐⭐⭐ |
| `useEffect` | 副作用 | ⭐⭐⭐⭐⭐ |
| `useContext` | 跨组件共享状态 | ⭐⭐⭐⭐ |
| `useReducer` | 复杂状态逻辑 | ⭐⭐⭐ |
| `useMemo` | 缓存计算结果，性能优化 | ⭐⭐⭐ |
| `useCallback` | 缓存函数，性能优化 | ⭐⭐⭐ |
| `useRef` | 引用 DOM 元素或保存可变值 | ⭐⭐⭐⭐ |

### 动手练习

- [ ] 写一个计数器（点击 +1/-1，显示当前数字）
- [ ] 写一个输入框，实时显示输入的内容（受控组件）
- [ ] 写一个 Todo List（添加、删除、标记完成）
- [ ] 用 useEffect 实现一个倒计时（从 10 到 0）
- [ ] 用 useEffect 请求一个公开 API 并显示数据

### 常见困惑

> **Q: 为什么直接修改 state 不生效？**
> A: React 靠 setState 来触发重新渲染。直接改对象/数组的属性，React 检测不到变化。

> **Q: useEffect 为什么会执行两次？**
> A: React 18 的严格模式（StrictMode）下，开发环境中组件挂载会执行两次，用来帮助你发现 bug。生产环境不会。

> **Q: useEffect 的依赖数组到底怎么写？**
> A: 把 effect 里用到的所有外部变量都放进去。ESLint 会提示你，听它的。

---

## 第三阶段：组件设计与通信（1 周）

### 学习目标

- 掌握组件间数据传递的各种方式
- 学会拆分组件，设计合理的组件结构

### 学习内容

#### 3.1 组件通信方式

| 通信方式 | 场景 | 实现方式 |
|---------|------|---------|
| **父 → 子** | 父传数据给子 | Props |
| **子 → 父** | 子通知父事件 | 回调函数（父传函数 prop 给子） |
| **兄弟之间** | 同级组件通信 | 状态提升（提升到共同父组件） |
| **跨多层** | 祖先传后代 | Context API |
| **全局状态** | 任何组件之间 | 状态管理库（Zustand、Redux 等） |

#### 3.2 状态提升

当多个组件需要共享状态时，把状态提升到它们最近的共同父组件。

```
        ┌──────────┐
        │  Parent  │  ← 状态放在这里
        └────┬─────┘
       ┌─────┴─────┐
       ↓           ↓
┌──────────┐ ┌──────────┐
│ Child A  │ │ Child B  │  ← 通过 props 接收状态
└──────────┘ └──────────┘
```

#### 3.3 Context API

跨多层组件传数据时用，避免一层一层传 props（prop drilling）。

```jsx
// 1. 创建 Context
const ThemeContext = createContext('light');

// 2. Provider 包裹组件
<ThemeContext.Provider value="dark">
  <App />
</ThemeContext.Provider>

// 3. 任意深层组件中使用
const theme = useContext(ThemeContext);
```

#### 3.4 组件设计原则

| 原则 | 说明 |
|------|------|
| **单一职责** | 一个组件只做一件事 |
| **可复用性** | 把可复用的部分抽成组件 |
| **Props 驱动** | 组件通过 props 接收数据，不要依赖外部变量 |
| **状态放哪里** | 放在需要它的组件的最近共同祖先 |
| **受控 vs 非受控** | 表单组件推荐用受控组件（state 控制 value） |

### 动手练习

- [ ] 把之前的 Todo List 拆分成多个组件（TodoInput、TodoList、TodoItem、TodoFilter）
- [ ] 实现一个选项卡组件（Tabs），点击切换显示不同内容
- [ ] 用 Context 实现主题切换（亮色/暗色）
- [ ] 写一个表单组件（用户名、密码、确认密码、提交按钮）

---

## 第四阶段：路由与数据请求（1 周）

### 学习目标

- 掌握 React Router 的使用
- 学会网络请求和数据处理

### 学习内容

#### 4.1 React Router v6

| 知识点 | 说明 | 重要程度 |
|--------|------|---------|
| **基础路由** | BrowserRouter、Routes、Route | ⭐⭐⭐⭐⭐ |
| **导航** | Link、NavLink、useNavigate | ⭐⭐⭐⭐⭐ |
| **动态路由** | `/user/:id` + useParams | ⭐⭐⭐⭐⭐ |
| **嵌套路由** | 子路由 + Outlet | ⭐⭐⭐⭐ |
| **重定向** | Navigate | ⭐⭐⭐ |
| **路由守卫** | 登录拦截（自定义组件实现） | ⭐⭐⭐⭐ |

#### 4.2 网络请求

| 方案 | 说明 | 推荐 |
|------|------|------|
| **Fetch API** | 浏览器内置，不需要额外安装 | 入门 |
| **Axios** | 功能更全：拦截器、取消请求、自动 JSON 解析 | ⭐⭐⭐⭐⭐ 推荐 |

#### 4.3 数据加载模式

| 模式 | 说明 |
|------|------|
| **组件挂载时请求** | useEffect + 空依赖数组 |
| **加载状态** | 请求中显示 loading，成功显示数据，失败显示错误 |
| **错误处理** | try/catch 或 .catch() |
| **请求取消** | AbortController（组件卸载时取消请求） |

### 动手练习

- [ ] 用 React Router 搭一个多页面应用（首页、列表、关于）
- [ ] 实现列表页 → 详情页（带 id 参数）
- [ ] 用 Axios 请求一个公开 API 并展示数据
- [ ] 添加加载状态、错误状态、重试按钮

---

## 第五阶段：状态管理库与进阶（1-2 周）

### 学习目标

- 了解主流状态管理方案，选一个深入学习
- 学习性能优化和工程化知识

### 学习内容

#### 5.1 状态管理库（选一个学）

| 库 | 特点 | 推荐指数 | 学习难度 |
|----|------|---------|---------|
| **Zustand** | 极简、轻量、API 最少，上手最快 | ⭐⭐⭐⭐⭐（新手推荐） | 低 |
| **Redux Toolkit** | 官方推荐、生态完善、调试工具强 | ⭐⭐⭐⭐ | 中 |
| **Jotai** | 原子化状态管理，类似 useState 的升级版 | ⭐⭐⭐ | 低 |
| **MobX** | 响应式，代码少但有学习曲线 | ⭐⭐⭐ | 中高 |

> **新手推荐 Zustand**：API 最简单，概念最少，几分钟就能上手。

#### 5.2 性能优化

| 优化点 | 说明 | 重要程度 |
|--------|------|---------|
| **React.memo** | 包裹组件，props 没变就不重新渲染 | ⭐⭐⭐ |
| **useMemo** | 缓存计算结果 | ⭐⭐⭐ |
| **useCallback** | 缓存函数引用 | ⭐⭐⭐ |
| **React DevTools Profiler** | 分析渲染性能瓶颈 | ⭐⭐⭐⭐ |
| **代码分割** | React.lazy + Suspense，按需加载 | ⭐⭐⭐ |
| **列表优化** | 虚拟列表（react-window） | ⭐⭐ |

> 注意：不要过早优化。先让代码跑起来，有性能问题再优化。

#### 5.3 其他进阶主题

| 主题 | 说明 |
|------|------|
| **自定义 Hook** | 把可复用的逻辑抽成自定义 Hook |
| **TypeScript 进阶** | 泛型、工具类型、条件类型 |
| **表单库** | React Hook Form、Formik（复杂表单用） |
| **数据获取库** | React Query / SWR（服务端状态管理） |
| **CSS in JS** | styled-components、Emotion |
| **Tailwind CSS** | 原子化 CSS 框架，非常流行 |
| **单元测试** | Jest + React Testing Library |

### 动手练习

- [ ] 用 Zustand 重构 Todo List 的状态管理
- [ ] 写一个自定义 Hook（如 `useLocalStorage`、`useFetch`）
- [ ] 用 React Query 管理数据请求和缓存
- [ ] 用 React DevTools Profiler 分析并优化性能

---

## 🎯 推荐学习资源

### 官方文档（最推荐）

- [React 官方文档（中文）](https://zh-hans.react.dev/) — 写得非常好，从头看到尾都没问题
- [React 学习之路](https://zh-hans.react.dev/learn) — 官方的交互式教程

### 视频教程

- [React 官方教程视频](https://www.youtube.com/watch?v=j942wKiXFu8) — YouTube
- B 站搜索"React 教程"，选播放量高的最新版本

### 练习平台

- [React 官方 Tic-Tac-Toe 教程](https://zh-hans.react.dev/learn/tutorial-tic-tac-toe) — 边做边学
- [Codewars](https://www.codewars.com/) — 刷题练习
- [Exercism](https://exercism.org/tracks/javascript) — 编程练习

### 博客与社区

- [React 博客](https://zh-hans.react.dev/blog) — 官方更新动态
- [掘金 React 标签](https://juejin.cn/tag/React) — 中文社区

---

## 💡 给 React 小白的建议

1. **一定要动手写**：看 10 遍视频不如自己写 1 遍
2. **从官方文档开始**：React 官方文档写得非常棒，是最好的入门资源
3. **先会用再深入**：不要纠结原理，先跑起来再说
4. **Hooks 是重中之重**：useState 和 useEffect 必须非常熟练
5. **组件拆分是艺术**：多拆组件，练习组件设计思维
6. **遇到报错先读错误信息**：React 的报错提示很友好，仔细读
7. **学完 React 再学 React Native**：React 基础扎实了，React Native 上手非常快

---

## 📅 学习计划模板（每日 1.5 小时）

| 周次 | 阶段 | 每日任务 |
|------|------|---------|
| 第 1-2 天 | 前置知识 | 复习 JS 基础（箭头函数、map、解构、Promise） |
| 第 3-7 天 | 第 1 阶段 | 每天学 2-3 个新概念，跟着写小例子 |
| 第 2 周 | 第 2 阶段 | 重点攻克 useState 和 useEffect，做 Todo List |
| 第 3 周 | 第 3 阶段 | 练习组件拆分和通信，写一个完整小项目 |
| 第 4 周 | 第 4 阶段 | 学路由和网络请求，接真实 API |
| 第 5-6 周 | 第 5 阶段 | 学状态管理库，做性能优化，写一个完整项目 |

---

## 下一步：过渡到 React Native

当你掌握了 React 基础后，学习 React Native 会非常快，因为：

- ✅ 组件化思想完全一样
- ✅ Hooks（useState、useEffect 等）完全一样
- ✅ 状态管理方案完全一样
- ✅ TypeScript 用法完全一样

主要的不同点：

| React (Web) | React Native |
|-------------|--------------|
| `<div>` | `<View>` |
| `<span>` / `<p>` | `<Text>` |
| `<img>` | `<Image>` |
| CSS | StyleSheet（Flexbox） |
| 浏览器事件（onClick） | 移动端手势（onPress） |
| React Router | Expo Router |
| DOM 操作 | 没有 DOM |

所以学好了 React，React Native 只需要学一下组件和 API 的差异，1-2 周就能上手开发。