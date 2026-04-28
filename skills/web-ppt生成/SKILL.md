---
name: web-ppt生成
description: |
  网页版在线PPT演示文稿生成技能。当用户提到以下情况时务必使用此技能：
  - 创建可在浏览器中展示的HTML演示文稿
  - 使用reveal.js、pptxgenjs等框架生成网页版PPT
  - 创建在线演示文稿
  - 生成可分享的网页PPT
  - 制作网页版幻灯片
  - 用户说"创建网页PPT"、"生成在线演示文稿"、"做reveal.js幻灯片"等
compatibility: html, css, javascript, reveal.js, pptxgenjs
---

# Web-PPT 在线演示文稿生成

## 核心能力

此技能使Claude能够创建可在浏览器中展示的HTML演示文稿，支持使用reveal.js等流行框架。

## 使用 reveal.js 创建演示文稿

### 基础HTML结构

```html
<!DOCTYPE html>
<html lang="zh-CN">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>演示文稿标题</title>
  <link rel="stylesheet" href="https://cdn.jsdelivr.net/npm/reveal.js@4.5.0/dist/reveal.css">
  <link rel="stylesheet" href="https://cdn.jsdelivr.net/npm/reveal.js@4.5.0/dist/theme/white.css">
  <style>
    .reveal { font-family: "Microsoft YaHei", "Heiti SC", sans-serif; }
    .reveal h1, .reveal h2, .reveal h3 { color: #333; }
    .reveal section { text-align: center; }
  </style>
</head>
<body>
  <div class="reveal">
    <div class="slides">
      <!-- 幻灯片内容 -->
    </div>
  </div>
  <script src="https://cdn.jsdelivr.net/npm/reveal.js@4.5.0/dist/reveal.js"></script>
  <script>
    Reveal.initialize();
  </script>
</body>
</html>
```

### 添加幻灯片

```html
<section>
  <h1>第一页标题</h1>
  <p>副标题内容</p>
</section>

<section>
  <h2>第二页</h2>
  <ul>
    <li>要点1</li>
    <li>要点2</li>
    <li>要点3</li>
  </ul>
</section>

<section>
  <h2>带图片的页面</h2>
  <img src="图片URL" alt="描述">
</section>

<section>
  <h2>分栏布局</h2>
  <div style="display: flex; justify-content: space-around;">
    <div>左栏内容</div>
    <div>右栏内容</div>
  </div>
</section>
```

### 常用效果

```html
<section data-transition="slide">滑入效果</section>
<section data-transition="fade">淡入淡出</section>
<section data-transition="convex">凸出效果</section>

<section class="fragment">逐步显示的内容1</section>
<section class="fragment">逐步显示的内容2</section>

<section>
  <span class="fragment highlight-red">红</span>
  <span class="fragment highlight-blue">蓝</span>
</section>
```

## 使用 pptxgenjs 创建

```javascript
const pptxgen = require("pptxgenjs");

let pres = new pptxgen();
let slide = pres.addSlide();

slide.addText("标题", {
  x: 0.5, y: 0.5, w: 9, h: 1,
  fontSize: 44, bold: true, color: "333333"
});

slide.addText([
  { text: "第一点\n", options: { bullet: true } },
  { text: "第二点\n", options: { bullet: true } },
  { text: "第三点", options: { bullet: true } }
], { x: 1, y: 2, w: 8, h: 3, fontSize: 20 });

slide.addImage({ data: "base64...", x: 2, y: 4, w: 6 });

pres.writeFile({ fileName: "presentation.pptx" });
```

## 主题配置

```html
<link rel="stylesheet" href="https://cdn.jsdelivr.net/npm/reveal.js@4.5.0/dist/theme/black.css">
<link rel="stylesheet" href="https://cdn.jsdelivr.net/npm/reveal.js@4.5.0/dist/theme/white.css">
<link rel="stylesheet" href="https://cdn.jsdelivr.net/npm/reveal.js@4.5.0/dist/theme/league.css">
<link rel="stylesheet" href="https://cdn.jsdelivr.net/npm/reveal.js@4.5.0/dist/theme/beige.css">
```

## 自定义样式

```html
<style>
  .reveal .slides section {
    background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
  }
  .reveal h1 { color: #fff; text-shadow: 2px 2px 4px rgba(0,0,0,0.3); }
  .reveal h2 { color: #fff; }
  .reveal p { color: #fff; font-size: 1.2em; }
  .reveal ul li { color: #fff; margin: 0.5em 0; }
  .reveal .footer { position: absolute; bottom: 20px; right: 20px; font-size: 0.4em; color: rgba(255,255,255,0.7); }
</style>
```

## 幻灯片布局技巧

```html
<section>
  <div style="display: flex; align-items: center; justify-content: center; height: 100%;">
    <div style="width: 45%; text-align: left;">
      <h2>左侧标题</h2>
      <p>左侧内容</p>
    </div>
    <div style="width: 45%;">
      <img src="图片URL" style="max-width: 100%;">
    </div>
  </div>
</section>

<section>
  <div style="display: grid; grid-template-columns: repeat(3, 1fr); gap: 20px;">
    <div>卡片1</div>
    <div>卡片2</div>
    <div>卡片3</div>
  </div>
</section>
```

## 最佳实践

1. **简洁设计**：每页聚焦一个核心信息
2. **视觉层次**：使用对比色和大小区分标题与正文
3. **适当留白**：避免内容过于拥挤
4. **统一风格**：保持整体配色和字体一致
5. **测试兼容性**：在不同浏览器中测试效果

## 常用reveal.js配置

```javascript
Reveal.initialize({
  hash: true,
  slideNumber: true,
  transition: 'slide',
  transitionSpeed: 'default',
  backgroundTransition: 'fade',
  center: true,
  width: 1920,
  height: 1080,
  margin: 0.1,
  controls: true,
  progress: true
});
```

## 示例任务

- "创建一个关于产品介绍的reveal.js演示文稿，包含5页"
- "生成一个带渐变背景和动画效果的在线PPT"
- "制作一个可分享的公司介绍网页幻灯片"
- "用reveal.js创建一个包含图表的月度汇报演示文稿"
