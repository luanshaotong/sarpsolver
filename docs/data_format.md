# 数据格式

## 输入样例

meta.json

{
    "mode": "normal",
	"attribute_dim_size": 3,
	"container_num": 10,
	"item_num": 10，
    "parameters":
    {
        "thread_num": 12,
        "pruning_rate": 0.5,
        "temperature_increasing_rate": 0
    }
}


containers.csv

| 容器种类编号 | 数量 | 成本权重 | 维度1容量 | 维度2容量 | 维度3容量 | ...
| string | positive integer | positive real | positive integer | positive integer | positive integer |

数量是对该类容器数量的一个估计上界，算法会从该数量向下优化，不会增加。
容量为整数，如果原始数据为实数请自行放大进行离散化，只要不超过2^31即可。

items.csv

| 货物种类编号 | 数量 | 价值权重 | 维度1占用 | 维度2占用 | 维度3占用 | ...
| string | positive integer | positive real | positive integer | positive integer | positive integer |

ab_constraints.csv

| 容器种类编号 | 货物种类编号 | 货物数量限制 |
| string | string | non-negative integer |

bb_constraints.csv

| 货物种类编号1 | 货物种类编号2 | 货物2数量限制 |
| string | string | non-negative integer |

## 输出样例

result.csv

| 货物种类编号 | 容器种类编号 |
| string | string |