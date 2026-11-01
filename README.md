# xiaomao-illustrations · 小猫怪诞正文配图 skill

给 Claude Code(或任何支持 skill 的 agent)的中文文章配图 skill。丢一篇文章进来,它负责想配图点、出 shot list、写英文提示词、逐张生成、自检迭代——产出一套白底手绘小猫风格的 16:9 正文配图。

> 改编自 [helloianneo/xiaomao-illustrations](https://github.com/helloianneo/xiaomao-illustrations)(MIT)。改动:IP 小黑 → 黑色小猫;生图出口通用化。方法论(五步工作流 / 构图模式 / QA / 风格 DNA / 提示词模板)保持上游原文。

## 装上

```bash
git clone https://github.com/fangtang951210/xiaomao-illustrations.git \
  ~/.claude/skills/xiaomao-illustrations
```

国内镜像(Gitee):

```bash
git clone https://gitee.com/cubesugar951210/xiaomao-illustrations.git \
  ~/.claude/skills/xiaomao-illustrations
```

装完不用配置。SKILL.md 的 frontmatter 会自动注册触发词。

## 用

对 agent 说人话即可:

- "给这篇文章配图" + 文章路径 → 出 shot list(配图策略)
- "生成配图" → 逐张生成(用你环境里可用的生图工具;有 ComfyArt MCP 走 generate_image,没有就走别的出口)

风格一句话:纯白背景、黑色手绘线稿、大量留白、少量红橙蓝中文批注、黑色小猫认真做一件荒诞但成立的事。不是 PPT 信息图,不是可爱卡通。

## 目录

```
SKILL.md                        # 入口:五步工作流 + 触发词
references/style-dna.md         # 风格底线
references/xiaohei-ip.md        # 小猫 IP(外形/性格/动作库/禁止)
references/composition-patterns.md  # 8 种构图 + 原创隐喻生成法
references/prompt-template.md   # 生图提示词模板(英文)
references/qa-checklist.md      # 生成后自检
```

## License

MIT(上游版权与本次改动声明见 LICENSE)。
