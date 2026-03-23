# Typst 模板结构说明

## 模板路径

`C:\Users\15pro\Downloads\ZJU-simpleLabReport-Typst-main`

## 预期表头结构

```typst
#let header = (
  course: "",           // 课程名称 - 留空
  name: "",       // 姓名
  student-id: "", // 学号
  location: "",  // 地点
  date: datetime.today(), // 日期 - 自动
  teacher: "",          // 指导老师 - 留空
  grade: "",            // 成绩 - 留空
  experiment-name: "",  // 实验名称 - 留空
  experiment-type: "",  // 实验类型 - 留空
  partner: "",          // 同族学生姓名 - 留空
)
```

## 预期章节结构

```typst
= 实验目的和要求

= 实验内容和原理

= 主要仪器设备

= 操作方法和实验步骤

= 实验数据记录和处理

= 实验结果与分析

= 思考与讨论
```

## 图片排版示例

### 同组横排（使用 grid）

```typst
#figure(
  grid(
    columns: (1fr, 1fr),
    image("V_1_1.png"),
    image("V_1_2.png"),
  ),
  caption: [图 1-1: 输入输出波形]
)
```

### 分组展示（使用子标题区分）

```typst
=== 第一组测量

#figure(
  grid(
    columns: (1fr, 1fr),
    image("V_1_1.png"),
    image("V_1_2.png"),
  ),
  caption: [输入输出波形]
)

=== 第二组测量

#figure(
  grid(
    columns: (1fr, 1fr),
    image("V_2_1.png"),
    image("V_2_2.png"),
  ),
  caption: [增益曲线]
)
```

## 数据表格示例

```typst
#figure(
  table(
    columns: (1fr, 1fr, 1fr),
    [频率 (Hz)], [U₁ (V)], [U₂ (V)],
    [100], [2.00], [1.98],
    [1000], [2.00], [1.95],
    [10000], [2.00], [1.85],
  ),
  caption: [表 1: 频率响应数据]
)
```
