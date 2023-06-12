### 配置提交规范

一个使用 husky 和 commitlint 来规定提交规范的 Demo

### husky

一个使用 git hook 的库，可以在提交前跑一些脚本整理提交信息，比如运行测试、lint 代码等。Husky 支持所有 Git 钩子
[https://typicode.github.io/husky/](https://typicode.github.io/husky/)

install husky

```shell
npm install husky --save-dev
```

### commitlint

```shell
# Install and configure if needed
npm install --save-dev @commitlint/{cli,config-conventional}
# For Windows:
npm install --save-dev @commitlint/config-conventional @commitlint/cli
```

添加钩子

```shell
npx husky add .husky/commit-msg  'npx --no -- commitlint --edit ${1}'
```

随后在项目根目录下创建文件 commitlint.config.js 配置规则
具体规则看官网，demo 简单的配置了个

```js
module.exports = {
  extends: ["@commitlint/config-conventional"],
  rules: {
    // 限制提交type只能为feat、fix、doc中其中一个
    "type-enum": [2, "always", ["feat", "fix", "doc"]],
  },
};
```
