---
name: excel数据分析
description: |
  Excel数据分析和可视化技能。当用户提到以下情况时务必使用此技能：
  - 读取Excel文件并分析数据
  - 生成数据图表（柱状图、折线图、饼图、散点图等）
  - 进行统计分析（求和、平均值、最大最小值、标准差等）
  - 创建数据透视表
  - 生成统计报表
  - Excel数据可视化
  - 分析销售数据、财务数据、调查数据等
  - 用户说"分析这个Excel文件"、"生成图表"、"数据可视化"等
compatibility: python, openpyxl, pandas, matplotlib, seaborn
---

# Excel 数据分析与可视化

## 核心能力

此技能使Claude能够读取Excel文件，进行数据分析，并生成可视化图表。

## 工作流程

### 1. 读取Excel文件

使用`openpyxl`或`pandas`读取Excel文件：

```python
import pandas as pd

df = pd.read_excel('文件路径.xlsx')
df = pd.read_excel('文件路径.xlsx', sheet_name='Sheet1')
```

### 2. 数据分析

根据用户需求进行数据分析：

```python
df.describe()

df['列名'].sum()
df['列名'].mean()
df['列名'].max()
df['列名'].min()

df.groupby('列名').agg({'数值列': 'sum'})
```

### 3. 生成图表

使用`matplotlib`和`seaborn`生成图表：

```python
import matplotlib.pyplot as plt
import seaborn as sns

plt.rcParams['font.sans-serif'] = ['SimHei', 'Microsoft YaHei']
plt.rcParams['axes.unicode_minus'] = False

plt.figure(figsize=(10, 6))
df.groupby('类别')['数值'].sum().plot(kind='bar')
plt.title('标题')
plt.savefig('chart.png', dpi=150, bbox_inches='tight')

plt.figure(figsize=(10, 6))
df.plot(x='日期', y='数值')
plt.title('趋势图')
plt.savefig('line_chart.png', dpi=150, bbox_inches='tight')

plt.figure(figsize=(8, 8))
df['列名'].value_counts().plot(kind='pie', autopct='%1.1f%%')
plt.title('占比分布')
plt.savefig('pie_chart.png', dpi=150, bbox_inches='tight')
```

### 4. 输出结果

将分析结果和图表保存到用户指定位置。

## 图表类型选择指南

| 数据关系 | 推荐图表 |
|---------|---------|
| 趋势变化 | 折线图 |
| 比较大小 | 柱状图 |
| 占比分布 | 饼图 |
| 相关关系 | 散点图 |
| 分布情况 | 直方图、箱线图 |

## 最佳实践

1. **明确分析目标**：在开始前确认用户想要什么样的分析结果
2. **数据预览**：先查看数据结构，了解有哪些列和数据类型
3. **选择合适的图表**：根据数据特点和分析目的选择最合适的可视化方式
4. **添加标签和标题**：确保图表有清晰的标题、轴标签和图例
5. **保持简洁**：避免过度装饰，聚焦于数据本身

## 示例任务

- "分析这个销售数据Excel文件，生成月度销售趋势图"
- "读取test.xlsx，计算各部门工资总和并生成柱状图"
- "对这个财务数据进行统计分析，生成报表和可视化图表"
