# github 提交规范

## 遇到的问题

1. 版本回退时无法快速定位到版本

2. 无法知道项目中封版操作是哪一个commit

3. 无法清晰的知道每次提交的记录

####以下是commit提交规范

每次提交，Commit message 都包括三个部分：Header，Body 和 Footer。

其中，Header 是必需的，Body 和 Footer 可以省略。

```
    <type>: (<scope>): <subject>
    // 空一行
    <body>
    // 空一行
    <footer>
```

## Header

Header部分只有一行，包含两个字段 `type`(必须) 和 `subject`(必须)

`type` 用于说明 `commit` 的类别，只允许使用下面8个标识。

```js
|    1. feat: 新功能（feature）
|    2. fix: 修补bug
|    3. docs: 文档（documentation）
|    4. style:  格式（不影响代码运行的变动）
|    5. refactor(ref): 重构（即不是新增功能，也不是修改bug的代码变动）
|    6. test: 增加测试
|    7. chore: 构建过程或辅助工具的变动
|    8. tag: 针对与每次版本的提交
|    9. revert: 撤销，版本回退
|   10. perf: 性能优化
```

`subject` 是 `commit` 目的的简短描述，不超过50个字符

```js
// 示例
example: 订单详情增加导出功能
```

`scope` 用于说明 commit 影响的范围，比如数据层、控制层、视图层等等，视项目不同而不同。

## Body

Body 部分是对本次 commit 的详细描述，可以分成多行。下面是一个范例。

```
xxx/xxx.tsx  修改内容
xxx/xxx.tsx  修改内容
```

## Footer

Footer 部分只用于两种情况。

1. 不兼容变动

如果当前代码与上一个版本不兼容，则 Footer 部分以 `BREAKING CHANGE`开头，后面是对变动的描述、以及变动理由和迁移方法。

```
BREAKING CHANGE: 项目webpack升级到4.0版本
xx插件替换成xx插件
```

2. 关闭 bug/需求

```
closes 3056, 11231
```

## Revert

还有一种特殊情况，如果当前 commit 用于撤销以前的 commit，则必须以`revert:`开头，后面跟着被撤销 Commit 的 Header

```
[revert](pencil): 回退当前版本 667ec 到 6c7ec
```

## 建议

​ 在平时提交fix和feat时，一般使用简写

```
    feat: 增加订单详情  closes xxxx (closes非必需)
    fix: 修复xx情况下xx问题  closes xxxx (closes非必需)
    docs: 修改md文件
    style: 修改订单列表样式
    ref: 重构utils.js下部分方法
    chore: 增加xxx插件/xxxxloader
    tag: 新建版本分支xxx
    revert: 回退当前版本667ec到 6c7ec
    perf:  优化了xxx，提高了渲染速度
```

在某些复杂commit比如 revert，chore 等操作时最好在body，footer，描述清楚 遇到了什么问题，为何要这样做

```
revert:(订单模块): 回退当前版本 667ec到 6c7ec

因为某次提交失误，造成xxx问题
xxx.tsx
xxx.less

closes xxx
```
