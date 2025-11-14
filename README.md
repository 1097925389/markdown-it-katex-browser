# Markdown-it-KaTeX Browser Plugin

一个用于 markdown-it 的 KaTeX 数学公式渲染插件，支持在浏览器环境中直接使用。

## 特性

- ✅ **浏览器友好**: 无需构建工具，直接在浏览器中使用
- ✅ **完整功能**: 支持行内数学公式和块级数学公式
- ✅ **多种语法**: 支持多种数学公式语法格式
- ✅ **高性能**: 基于 KaTeX 的快速渲染
- ✅ **灵活配置**: 支持多种配置选项

## 支持的数学公式语法

### 行内公式
- `$...$` - 标准行内公式语法
- `` `$...$` `` - 反引号包围的行内公式

### 块级公式
- `$$...$$` - 标准块级公式语法
- LaTeX 环境语法: `\begin{align}...\end{align}` 等
- 代码块语法: ````math ... ````

### HTML 中的数学公式
- 支持在 HTML 块中识别和渲染数学公式
- 支持行内和块级公式混合使用

## 安装使用

### 1. 下载文件
下载 `markdown-it-katex.min.js` 文件到你的项目中。

### 2. 引入依赖
在 HTML 中引入必要的依赖：

```html
<!-- KaTeX CSS -->
<link rel="stylesheet" href="https://cdn.jsdelivr.net/npm/katex@0.16.0/dist/katex.min.css">

<!-- KaTeX JavaScript -->
<script src="https://cdn.jsdelivr.net/npm/katex@0.16.0/dist/katex.min.js"></script>

<!-- markdown-it -->
<script src="https://cdn.jsdelivr.net/npm/markdown-it@13.0.0/dist/markdown-it.min.js"></script>

<!-- 本插件 -->
<script src="./markdown-it-katex.min.js"></script>
```

### 3. 使用插件

```javascript
// 创建 markdown-it 实例并使用插件
const md = markdownit().use(markdownItKatex);

// 渲染包含数学公式的 Markdown
const result = md.render(`
# 数学公式示例

行内公式：$E = mc^2$

块级公式：
$$
\\int_{-\\infty}^{\\infty} e^{-x^2} dx = \\sqrt{\\pi}
$$

矩阵：
$$
\\begin{pmatrix}
a & b \\\\
c & d
\\end{pmatrix}
$$
`);

document.getElementById('output').innerHTML = result;
```

## 配置选项

插件支持以下配置选项：

```javascript
const md = markdownit().use(markdownItKatex, {
  // KaTeX 配置选项
  throwOnError: false,           // 遇到错误时不抛出异常
  displayMode: false,            // 默认显示模式
  
  // 插件特定选项
  enableBareBlocks: true,        // 启用裸露的 LaTeX 块（如 \begin{align}）
  enableMathBlockInHtml: true,   // 启用 HTML 块中的数学公式
  enableMathInlineInHtml: true,  // 启用 HTML 行内数学公式
  enableFencedBlocks: true       // 启用围栏代码块中的数学公式
});
```

## 示例

### 基本使用示例

```html
<!DOCTYPE html>
<html>
<head>
    <title>Markdown-it-KaTeX 示例</title>
    <link rel="stylesheet" href="https://cdn.jsdelivr.net/npm/katex@0.16.0/dist/katex.min.css">
</head>
<body>
    <div id="output"></div>

    <script src="https://cdn.jsdelivr.net/npm/katex@0.16.0/dist/katex.min.js"></script>
    <script src="https://cdn.jsdelivr.net/npm/markdown-it@13.0.0/dist/markdown-it.min.js"></script>
    <script src="./markdown-it-katex.min.js"></script>
    
    <script>
        const md = markdownit().use(markdownItKatex);
        
        const markdown = `
        # 数学公式测试
        
        这是一个行内公式：$f(x) = x^2 + 2x + 1$
        
        这是一个块级公式：
        $$
        \\sum_{i=1}^{n} i = \\frac{n(n+1)}{2}
        $$
        `;
        
        document.getElementById('output').innerHTML = md.render(markdown);
    </script>
</body>
</html>
```

## 技术说明

本插件基于 [@vscode/markdown-it-katex](https://www.npmjs.com/package/@vscode/markdown-it-katex) 包进行浏览器适配，主要修改包括：

- 移除了 Node.js 模块系统依赖
- 改为 IIFE（立即执行函数表达式）格式
- 适配浏览器全局变量访问
- 保持完整的原始功能

## 兼容性

- 现代浏览器（支持 ES6+）
- markdown-it v12.0.0+
- KaTeX v0.13.0+

## 许可证

基于原项目许可证。

## 更新日志

### v1.0.0
- 初始版本
- 基于 @vscode/markdown-it-katex 的浏览器适配版本
- 支持完整的数学公式渲染功能
