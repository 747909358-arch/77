# 基础数据集数据字典

## A. 单列原子数据（计划）

保持不同变量分文件，不把单位或类别塞入数值列。

| 文件建议 | 单列字段 | 类型 | 单位/格式 | 一条记录代表什么 | 来源 | 状态 |
|---|---|---|---|---|---|---|
| plastic_item_category.csv | item_category | string | 类别名称 | 一个垃圾制品类别 | NOAA 分类体系/文献 | 待获取官方类别表 |
| river_emission_tonnes.csv | emission_tonnes_per_year | numeric | tonnes/year | 一个河流/流域在 2019 年的模型估计值 | S02 | 待下载与审字段 |
| shoreline_debris_count.csv | item_count | integer | count | 一个样点一次调查中的计数值（须与记录粒度配套） | S03 | 待导出与审字段 |
| impact_mechanism.csv | mechanism | string | 摄入/缠绕/栖息地等 | 一个文献记录的影响机制标签 | S01/同行评审研究 | 待文献编码 |

说明：上表是数据结构设计，不是已获得的数据；不得据此生成假数据。

## B. 多字段叙事数据（计划）

### 河流入海估计表
| 字段名 | 含义 | 类型 | 单位/格式 | 来源 |
|---|---|---|---|---|
| record_id | 唯一记录 ID | string | 唯一值 | 自建 |
| river_or_basin | 河流/流域名称 | string | 原始名称 | S02/原始论文 |
| country_or_region | 国家/区域 | string | 标准名称 | S02 |
| year | 指标年份 | integer | 2019 | S02 |
| estimated_emission | 入海估计量 | numeric | tonnes/year | S02 |
| estimate_method | 方法属性 | string | modelled estimate | S02 |
| size_scope | 粒径范围 | string | 原研究定义 | S02 |
| uncertainty_note | 不确定性说明 | string | 文本 | S02 |
| source_id | 来源 ID | string | S02 | 项目登记 |

### 海岸线监测表
| 字段名 | 含义 | 类型 | 单位/格式 | 来源 |
|---|---|---|---|---|
| survey_id | 调查记录 ID | string | 唯一值 | S03 |
| site_id | 监测点 ID | string | 原始 ID | S03 |
| latitude / longitude | 坐标 | numeric | decimal degrees | S03 |
| survey_date | 调查日期 | date | ISO 8601 | S03 |
| item_category | 垃圾类别 | string | 官方类别 | S03 |
| item_count | 计数 | integer | items | S03 |
| transect_length | 样带长度 | numeric | m | S03（如提供） |
| survey_effort | 调查努力量 | numeric/string | 原始定义 | S03 |
| source_id | 来源 ID | string | S03 | 项目登记 |

## C. 数据关联与质量规则
- 河流估计表和海岸线监测表保持独立；只有在空间、时间和指标定义匹配后才考虑关联。
- 地图中河流估计用流域/河流符号，海岸调查用点位符号；不得混用。
- 坐标系统一为 WGS84（EPSG:4326）前先检查原始 CRS。
- 保留原始名称和标准化名称两个字段；所有标准化映射写入清洗日志。
- 空值不自动填 0；区分未调查、未报告、不适用和真实零值。
- 数值保留原始单位，转换单位时增加新字段并记录公式。

## D. 许可与版本
每个文件记录 source_id、下载日期、来源版本、原始文件哈希（若可生成）、许可、处理脚本版本和清洗日期。
