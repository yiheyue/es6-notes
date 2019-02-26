# Module 的语法

## 概述

ES6 之前，JavaScript 一直没有模块系统，这使得 JavaScript 难以胜任开发大型项目的任务。为了解决这个问题，社区主要提出了两种模块加载方案：

1. CommonJS 规范 - 主要用于服务器

2. AMD 规范 - 主要用于浏览器

ES6 模块通过 `export` 显式指定输出的代码，再通过 `import` 输入。

## `export`

`export` 用于规定模块的对外接口。

1. 单独输出每一个变量

    ```js
    export let firstName = 'John'
    export let lastName = 'Snow'
    export let year = 2019
    ```

2. 一次输出所有的变量

    ```js
    let firstName = 'John'
    let lastName = 'Snow'
    let year = 2019

    export {
      firstName,
      lastName,
      year
    }
    ```

3. 输出函数或类

    ```js
    export funtion add2Num (a, b) {
      return a + b
    }

    // 使用 as 关键字重命名
    function add3Num (a, b, c) {
      return a + b + c
    }
    export {
      add3Num as add3
    }
    ```

## `import`

`import` 用于输入其他模块提供的功能。

- 加载指定模块

    ```js
    import { firstName, lastName, year } from './profile.js'

    // 使用 as 关键字重命名
    import { firstName as fname, lastName as lname, year } from './profile.js'
    ```

- 加载整个模块

    ```js
    // 使用 * 表示加载整个模块
    import * from './profile.js'
    ```

## `export default`

使用 `export default` 输出的模块，在 `import` 时可以使用任意自定义变量来访问它。

- 输出

    ```js
    // foo.js
    let message = 'Hello'
    let age = 22

    export default {
      message,
      age
    }
    ```

- 输入

    ```js
    import foo from 'foo.js'

    console.log(foo.message)
    ```

## 跨模块常量

- 示例

    ```js
    // constants.js
    export const A = 1
    export const B = 2
    export const C = 3

    // main.js
    import * as constant from './constants.js'
    console.log(constants.A)
    ```