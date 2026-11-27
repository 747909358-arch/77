# Gapminder 数据样本｜婴儿死亡率与人均收入

- 文件：`gapminder_infant_mortality_income_sample.csv`
- 性质：从公开数据集抽取的现代对照样本，不是 1930 年《Gesellschaft und Wirtschaft》的原始数据。
- 来源仓库：https://github.com/open-numbers/ddf--gapminder--systema_globalis
- 来源许可：CC BY 4.0（Gapminder 仓库声明）。
- 指标来源说明：婴儿死亡率字段来自 Gapminder 对多来源估计的汇编；其定义为每 1,000 名活产婴儿中第一年死亡数。Gapminder 自身说明部分序列含估算/插补，适合宏观可视化，不建议未经核验用于精密统计推断。
- 收入字段：`income_per_person_long_series`，Gapminder 的长期人均收入序列。该字段的精确版本与基准口径需结合对应版本的指标文档核对；本文件不自行推断未在字段中明确的基准年份。
- 抽取范围：12 个国家/地区代码，年份 1960、1970、1980、1990、2000、2010、2015；只保留源表中至少一个指标有值的国家-年份组合。
- 字段：`country_code`、`country_name`、`year`、`infant_mortality_rate_per_1000_births`、`income_per_person_long_series`。
- 清洗：按 `geo + time` 连接两个指标表；未对缺失值插补，缺失字段留空；不做单位转换。
- 署名：Data from Gapminder, Systema Globalis, CC BY 4.0. Original indicator sources are identified in Gapminder documentation.
- 重要限制：该数据样本只能用于现代示例、视觉编码测试或新设计任务；不能标注为 ISOTYPE 原作的 1930 年统计数据。
