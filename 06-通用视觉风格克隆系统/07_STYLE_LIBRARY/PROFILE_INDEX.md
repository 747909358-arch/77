# SC-IMG Pro｜可调用风格档案

| style_id | 名称 | 状态 | 证据边界 |
|---|---|---|---|
| STYLE-0001 | 哈里·贝克式地铁线路拓扑图 | draft | 公开领域来源页 + 已有文字分析；未进行本地像素测量 |
| STYLE-0002 | 马西莫·维涅里式网格化地铁线路图 | draft | CC BY 2.0 摄影记录页 + 已有文字分析；非原始设计母版 |
| STYLE-0003 | R2D3 式滚动渐进视觉叙事 | draft | 项目主页 + 已有文字分析；未逐屏复核 |
| STYLE-0004 | ISOTYPE 历史图像统计符号语言 | draft | 五个历史案例文字记录 + 方法文档；原图未获许可/未检查 |

## 调用方式

在 SC-IMG Pro 的 `apply` 模式中指定 `style_id`，并先读取对应 JSON。档案当前只适合作为研究草案和提示词初始条件；生成后必须创建 `image_task` 与 `image_review`，完成六维验收后才能升级为 validated。

## 证据原则

`observation`、`inference`、`user_requirement`、`design_choice` 分开记录。未检查的图像细节保持 pending，不从文字介绍推断具体色值、线宽、字体或材质。
