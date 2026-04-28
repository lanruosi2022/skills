---
name: word文本编写
description: |
  Word文档格式排版技能。当用户提到以下情况时务必使用此技能：
  - 创建Word文档并设置格式
  - 设置字体、字号、颜色
  - 设置段落格式（对齐、行间距、缩进）
  - 添加页眉页脚
  - 生成目录
  - 文档排版
  - 样式设置
  - 用户说"创建Word文档"、"排版"、"设置格式"等
compatibility: python, python-docx
---

# Word 文本编写与格式排版

## 核心能力

此技能使Claude能够创建专业的Word文档，并进行完整的格式排版。

## 工作流程

### 1. 创建文档基础结构

```python
from docx import Document
from docx.shared import Pt, Cm, RGBColor
from docx.enum.text import WD_ALIGN_PARAGRAPH, WD_LINE_SPACING
from docx.enum.style import WD_STYLE_TYPE

doc = Document()
```

### 2. 设置字体格式

```python
run = paragraph.add_run('文本内容')
run.font.name = '微软雅黑'
run.font.size = Pt(12)
run.font.bold = True
run.font.italic = False
run.font.color.rgb = RGBColor(0, 0, 0)
```

### 3. 设置段落格式

```python
paragraph = doc.add_paragraph()

paragraph.alignment = WD_ALIGN_PARAGRAPH.LEFT
paragraph.line_spacing_rule = WD_LINE_SPACING.ONE_POINT_FIVE
paragraph.first_line_indent = Cm(0.74)
paragraph.paragraph_format.space_before = Pt(0)
paragraph.paragraph_format.space_after = Pt(0)
```

### 4. 添加标题和样式

```python
doc.add_heading('一级标题', level=1)
doc.add_heading('二级标题', level=2)
doc.add_heading('三级标题', level=3)

body_style = doc.styles['Normal']
body_style.font.name = '宋体'
body_style.font.size = Pt(12)
```

### 5. 设置页眉页脚

```python
from docx.oxml.ns import qn

section = doc.sections[0]
header = section.header
header_para = header.paragraphs[0]
header_para.text = '页眉内容'
header_para.alignment = WD_ALIGN_PARAGRAPH.CENTER

footer = section.footer
footer_para = footer.paragraphs[0]
footer_para.text = '第X页'
footer_para.alignment = WD_ALIGN_PARAGRAPH.CENTER
```

### 6. 添加目录

```python
doc.add_page_break()
doc.add_heading('目录', level=1)
```

### 7. 添加图片和表格

```python
from docx.shared import Inches

doc.add_picture('图片路径.png', width=Inches(5))

table = doc.add_table(rows=3, cols=3)
table.style = 'Light Grid Accent 1'
```

### 8. 保存文档

```python
doc.save('输出文档.docx')
```

## 常用格式参数

### 字体设置
| 属性 | 说明 | 示例值 |
|-----|------|-------|
| font.name | 字体名称 | '微软雅黑', '宋体', 'Times New Roman' |
| font.size | 字号 | Pt(12), Pt(14), Pt(16) |
| font.bold | 加粗 | True/False |
| font.italic | 斜体 | True/False |
| font.color.rgb | 颜色 | RGBColor(0, 0, 0) |

### 段落设置
| 属性 | 说明 | 示例值 |
|-----|------|-------|
| alignment | 对齐 | WD_ALIGN_PARAGRAPH.LEFT/CENTER/RIGHT/JUSTIFY |
| line_spacing | 行距 | 1.5, 2.0, Pt(18) |
| first_line_indent | 首行缩进 | Cm(0.74)约两字符 |
| space_before | 段前间距 | Pt(0), Pt(6) |
| space_after | 段后间距 | Pt(0), Pt(6) |

## 最佳实践

1. **统一风格**：整个文档使用统一的字体和段落风格
2. **层级清晰**：合理使用标题级别，保持文档结构清晰
3. **适当留白**：合理设置行间距和段落间距，提高可读性
4. **中英混排**：中文使用宋体/微软雅黑，英文使用Times New Roman
5. **页眉页脚**：正式文档添加页眉页脚，包含页码和文档标题

## 示例任务

- "创建一份专业报告，包含标题、目录、正文和页眉页脚"
- "帮我排版这篇论文，设置首行缩进和1.5倍行距"
- "生成一个包含图片和表格的产品说明书"
