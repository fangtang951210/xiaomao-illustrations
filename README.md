# xiaomao-illustrations · 小猫怪诞正文配图 skill(+ qwen-image 提示词炼金)

给 Claude Code(或任何支持 skill 的 agent)的中文文章配图组合:丢一篇文章进来,agent 负责想配图点、出 shot list、写提示词、逐张生成、自检迭代——产出一套白底手绘小猫风格的 16:9 正文配图。

两个 skill 配套使用:

- **xiaomao-illustrations** — 配图策略与风格(五步工作流 / 构图模式 / QA / 风格 DNA)
- **qwen-image** — 提示词炼金(文生图"观察者报告"八步 / 图像编辑"改删保"指令),蒸馏自 Qwen Image 2.1 官方 PE system_prompt;本地部署 Qwen Image 2.1 的用户按它炼提示词,复现效果最好

> xiaomao-illustrations 改编自 [helloianneo/xiaomao-illustrations](https://github.com/helloianneo/xiaomao-illustrations)(MIT)。改动:IP 小黑 → 黑色小猫;生图出口通用化。方法论保持上游原文。

## 装上

```bash
git clone https://github.com/fangtang951210/xiaomao-illustrations.git /tmp/xm
cp -r /tmp/xm/xiaomao-illustrations /tmp/xm/qwen-image ~/.claude/skills/
```

国内镜像(Gitee):

```bash
git clone https://gitee.com/cubesugar951210/xiaomao-illustrations.git /tmp/xm
cp -r /tmp/xm/xiaomao-illustrations /tmp/xm/qwen-image ~/.claude/skills/
```

装完不用配置,frontmatter 自动注册触发词。两个 skill 独立可用,配套最佳。

## 用

对 agent 说人话:

- "给这篇文章配图" + 文章路径 → 出 shot list(配图策略)
- "生成配图" → 逐张生成。有 ComfyArt MCP 走 `generate_image`(qwen-image 的 SKILL.md 里写了模型流名),本地 Qwen Image 2.1 用户直接复现;没有就用环境里其他生图出口

风格一句话:纯白背景、黑色手绘线稿、大量留白、少量红橙蓝中文批注、黑色小猫认真做一件荒诞但成立的事。不是 PPT 信息图,不是可爱卡通。

## 案例展示

`examples/` 里 13 张全部由这条链产出:小猫 skill 出 shot list → qwen-image 炼提示词 → Qwen Image 2.1 生成。出自文章《用 Agent 的人和不用的人,已经不在同一个世界里了》(2026-10):

| 图 | 构图 | 讲什么 |
|---|---|---|
| 封面 | 概念隐喻 | 裂缝两侧各一只猫,两个世界 |
| 01 两个世界 | 概念隐喻 | 裂缝劈开地面,信息流两侧不对等 |
| 02 筛 | 系统局部 | 机器碾垃圾,只出三条干净信息 |
| 03 闸门 | 概念隐喻 | 小猫拧阀,每天 10 亿 Token 奔涌 |
| 04 三格漫画 | 小漫画分镜 | 我只要结果→它自己修→晾衣绳收片 |
| 05 五节点小路 | 地图路线 | 从开源项目到部署测试的学习路 |
| 06 两猫邮件 | Workflow | skill 从一只猫的机器飞进另一只的 |
| 07 日报井 | 概念隐喻 | 小猫探进井里挖校验过的信息 |
| 08 论文三状态 | 角色状态 | 看不懂→逐字解读→做成动画 |
| 09 分享欲出口 | 概念隐喻 | 折叠空间:上猫说话,下纸成摞 |
| 10 体温计170HX | 数据 | 5000 买入,2 万的水银柱 |
| 11 下雨回家 | 概念隐喻 | 伞下小猫抱书,伞外淋着 |
| 12 口喷成文 | 前后对比 | 口喷的乱线团被梳成文章 |

## 目录

```
xiaomao-illustrations/            # 配图 skill
├── SKILL.md                      # 入口:五步工作流 + 触发词 + qwen-image 衔接
└── references/                   # 风格DNA / 小猫IP / 构图模式 / 提示词模板 / QA
qwen-image/                       # 提示词炼金 skill
├── SKILL.md                      # 总纲(观察者纪律×10)
└── references/                   # t2i.md 八步炼法 / edit.md 改删保指令
examples/                         # 13 张真实产出案例
```

## License

MIT(上游版权与本次改动声明见 LICENSE)。
