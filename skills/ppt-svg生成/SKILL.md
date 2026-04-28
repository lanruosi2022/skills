---
name: ppt-svg生成
description: |
  SVG矢量图形制作技能，专为PPT演示文稿创建SVG图形。当用户提到以下情况时务必使用此技能：
  - 创建SVG图标（扁平化图标、线性图标、填充图标）
  - 制作SVG图表（柱状图、饼图、折线图的SVG版本）
  - 创建SVG流程图和示意图
  - 制作PPT用的矢量图形
  - 将数据可视化转为SVG格式
  - 用户说"创建SVG图标"、"制作矢量图形"、"生成SVG图表"等
compatibility: svg, xml, python, cairosvg
---

# PPT-SVG 矢量图形制作

## 核心能力

此技能使Claude能够创建高质量的SVG矢量图形，可直接导入PowerPoint或其他演示文稿工具使用。

## SVG基础结构

```xml
<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 100 100" width="100" height="100">
  <!-- 图形内容 -->
</svg>
```

## 常用SVG图形制作

### 1. 基础形状

```xml
<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 200 200" width="200" height="200">
  <rect x="10" y="10" width="80" height="80" fill="#4A90E2" rx="5"/>
  <circle cx="150" cy="50" r="40" fill="#E94B35"/>
  <line x1="10" y1="120" x2="190" y2="120" stroke="#333" stroke-width="2"/>
</svg>
```

### 2. 图标制作（以手机图标为例）

```xml
<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 24 24" width="24" height="24">
  <rect x="5" y="2" width="14" height="20" rx="2" fill="none" stroke="#333" stroke-width="1.5"/>
  <circle cx="12" cy="18" r="1" fill="#333"/>
  <line x1="9" y1="5" x2="15" y2="5" stroke="#333" stroke-width="1.5"/>
</svg>
```

### 3. 柱状图SVG

```xml
<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 400 300" width="400" height="300">
  <rect x="50" y="200" width="60" height="50" fill="#4A90E2"/>
  <rect x="130" y="150" width="60" height="100" fill="#4A90E2"/>
  <rect x="210" y="100" width="60" height="150" fill="#4A90E2"/>
  <rect x="290" y="50" width="60" height="200" fill="#4A90E2"/>
  <text x="80" y="270" text-anchor="middle" font-size="12">Q1</text>
  <text x="160" y="270" text-anchor="middle" font-size="12">Q2</text>
  <text x="240" y="270" text-anchor="middle" font-size="12">Q3</text>
  <text x="320" y="270" text-anchor="middle" font-size="12">Q4</text>
</svg>
```

### 4. 饼图SVG

```xml
<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 200 200" width="200" height="200">
  <circle cx="100" cy="100" r="80" fill="#4A90E2"/>
  <path d="M100,100 L100,20 A80,80 0 0,1 170,100 Z" fill="#E94B35"/>
  <path d="M100,100 L170,100 A80,80 0 0,1 100,180 Z" fill="#50C878"/>
</svg>
```

### 5. 流程图箭头

```xml
<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 100 60" width="100" height="60">
  <polygon points="0,30 70,30 70,20 100,30 70,40 70,30" fill="#333"/>
</svg>
```

## 使用Python生成SVG

```python
def create_bar_chart_svg(data, labels, output_path):
    max_value = max(data)
    bar_width = 60
    gap = 20
    width = len(data) * (bar_width + gap) + 100
    height = 300

    svg = f'''<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 {width} {height}" width="{width}" height="{height}">
    '''

    for i, (value, label) in enumerate(zip(data, labels)):
        bar_height = (value / max_value) * 200
        x = 50 + i * (bar_width + gap)
        y = height - 50 - bar_height
        svg += f'<rect x="{x}" y="{y}" width="{bar_width}" height="{bar_height}" fill="#4A90E2"/>\n'
        svg += f'<text x="{x + bar_width//2}" y="{height - 20}" text-anchor="middle" font-size="12">{label}</text>\n'

    svg += '</svg>'

    with open(output_path, 'w', encoding='utf-8') as f:
        f.write(svg)

data = [120, 200, 150, 180]
labels = ['Q1', 'Q2', 'Q3', 'Q4']
create_bar_chart_svg(data, labels, 'chart.svg')
```

## SVG图形导入PPT

1. 保存SVG文件
2. 在PowerPoint中：插入 → 图片 → 选择SVG文件
3. SVG作为矢量图形导入，可无损缩放

## 最佳实践

1. **使用viewBox**：设置合适的viewBox使图形可自由缩放
2. **扁平化设计**：PPT中扁平化风格更简洁专业
3. **统一配色**：使用2-3种主色调，保持视觉一致
4. **简洁清晰**：图形元素不宜过密，保持视觉清晰
5. **添加适当间距**：元素间保持足够间距，避免拥挤

## 颜色推荐（商务风格）

| 用途 | 颜色代码 | 说明 |
|-----|---------|------|
| 主色 | #4A90E2 | 蓝色 |
| 强调 | #E94B35 | 红色 |
| 成功 | #50C878 | 绿色 |
| 警告 | #F5A623 | 橙色 |
| 中性 | #333333 | 深灰 |

## 示例任务

- "创建一个表示增长趋势的SVG线性图标"
- "制作一个包含4个季度数据的SVG柱状图"
- "生成一个手机、邮件、电脑的SVG图标组合"
