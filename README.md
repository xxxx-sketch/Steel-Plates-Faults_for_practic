# Steel Plates Faults

钢板缺陷分类练习数据。判别分析要解决的问题是：根据钢板缺陷的多个检测特征，判断该样本属于哪一种缺陷类型。

## 因变量

缺陷类别：

```text
Y = FaultType
```

`FaultType` 是多分类类别变量，共 7 类：

- Pastry
- Z_Scratch
- K_Scatch
- Stains
- Dirtiness
- Bumps
- Other_Faults

原始 CSV 中这 7 类以 0/1 列给出，每一行通常只有一类为 1。使用前需要把它们合并成一个类别变量。

## 自变量

本练习使用 6 个连续型特征：

```text
X = (X1, X2, X3, X4, X5, X6)
```

| 变量 | R 变量名 | 含义 |
| --- | --- | --- |
| X1 | `Pixels_Areas` | 缺陷区域的像素面积，反映缺陷大小 |
| X2 | `X_Perimeter` | 缺陷在 X 方向的边界特征 |
| X3 | `Y_Perimeter` | 缺陷在 Y 方向的边界特征 |
| X4 | `Minimum_of_Luminosity` | 缺陷区域最小亮度 |
| X5 | `Maximum_of_Luminosity` | 缺陷区域最大亮度 |
| X6 | `Steel_Plate_Thickness` | 钢板厚度 |

完整的判别问题可以写成：

```text
FaultType = f(
  Pixels_Areas,
  X_Perimeter,
  Y_Perimeter,
  Minimum_of_Luminosity,
  Maximum_of_Luminosity,
  Steel_Plate_Thickness
)
```

## 数据文件

`faults.csv`：1941 条缺陷记录，34 列。除上面 6 个自变量和 7 个缺陷指示列外，还包含位置、周长、亮度等其他检测特征。本练习只使用表中的 6 个特征。

## 读取

```r
url <- "https://raw.githubusercontent.com/xxxx-sketch/Steel-Plates-Faults_for_practic/main/faults.csv"
df <- read.csv(url)
```

## 来源

数据整理自 [kitofficial/Faulty_steel_plates](https://github.com/kitofficial/Faulty_steel_plates) 中的 `faults.csv`。
