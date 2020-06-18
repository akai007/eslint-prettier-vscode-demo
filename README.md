### 前言
相信大家在接触不同项目参与开发时，已经领略过许多风格各异的代码风格，其中不乏结构清晰风格统一的优质代码，更多的时候我们会遇到在同一个项目中也可能是在同一个文件中风格迥异的代码，这个时候多少会让你无从下手然后按照自己的风格"锦上添花"。根本原因还是 javascript 本身对代码风格没有约束。但是在团队开发中这又是很需要的。


### 使用 eslint + prettier + vscode 自动格式化
所以使用 eslint 来作约束是很有必要的, 但由于 javascript 的风格实在是太多，而且迄今为止还有很多细节存在争议；另外由于遵循严格的风格有较高的学习成本和适应成本，像 Airbnb 的 eslint 也确实太过严格。所以 eslint + prettier + vscode 的整合能让代码在保存的时候自动格式化就很好的解决了这个矛盾。言归正传，下面就详细介绍一下这块的配置


### 配置 eslint + prettier + vscode
>安装 npm 相关包
1. 在对应文件夹初始化项目 `npm init` 如已有工程请忽略
2. `npm install eslint prettier --save-dev` 安装 eslint 以及 prettier
3. `npm install eslint-config-prettier eslint-plugin-prettier --save-dev` 安装相关插件

> 安装 vscode 插件 [ESLint](https://marketplace.visualstudio.com/items?itemName=dbaeumer.vscode-eslint) 和 [Prettier - Code formatter
](https://marketplace.visualstudio.com/items?itemName=esbenp.prettier-vscode)

> 添加配置.eslintrc.js
```

module.exports = {
  plugins: ['prettier'],
  rules: {
    'prettier/prettier': 'error',
  },
  extends: ['plugin:prettier/recommended'],
};

```

> 添加配置.prettierrc.js
```

module.exports = {
  printWidth: 120,
  tabWidth: 2,
  tabs: false,
  semi: true,
  singleQuote: true,
  quoteProps: 'as-needed',
  tailingComma: 'all',
  bracketSpacing: true,
  jsxBracketSameLine: false,
  arrowParens: 'always'
};

// 具体可以根据团队需要进行配置

```

> 添加 .vscode/settings.json 配置 (也可以配置到全局)
```
{
  "editor.codeActionsOnSave": {
    "source.fixAll.eslint": true
  }
}

```
