---
name: qwen-image
description: Write prompts for Qwen Image 2.1 before calling ComfyArt generate_image / remove_background. Two recipes: text-to-image distills one line into an observer report (eight steps); image editing distills plain speech into precise change-delete-keep instructions (attribute decoupling). Decide the type first, then write. Covers color and material discipline, frame walking with positions, literal-text survival, multi-image tags, ratio lookup.
---

# Qwen Image 2.1 提示词炼金

两套炼法:**文生图**(把一句话炼成"观察者报告",见 `references/t2i.md`)与**图像编辑**(把人话炼成"改删保指令",见 `references/edit.md`)。**先判类型再动笔**;两炼共用下方总纲。

判断:任务给了底图/参考图(要改、要合成、要换背景换装)→ 编辑流;只给了文字需求 → 文生图流。

## 总纲(共用写作纪律)

1. **观察者视角**:描述"画面里有什么",不写"要做什么"。现在时、陈述句;禁"你要/请生成/确保/画面应";禁空洞质量词(杰作、8K、超高清、获奖、大师级)
2. **用户钉死的逐字存活**:图内文字原文逐字保留(含标点空格)、点名的物体/数量/颜色/位置/比例,一个不许动
3. **元指令静默执行不回声**:"文字要清晰""不要硬边块""4K 无噪点"是对活儿的要求不是画面内容——照做,但别写进描述
4. **颜色必带修饰**:藏青、灰橄榄、奶油白、暖陶土、蓝灰、炭黑——几乎永不裸写"蓝色";用户给 hex 才用 hex
5. **材质必写**:拉丝金属、哑光塑料、亮釉陶瓷、粗麻、风化木、磨砂玻璃、纸纤维、水汽、划痕
6. **枚举不概括**:"若干物品/各种装饰"不算描述,逐个说;小数量用文字(三盏灯、五只鸟);被遮挡的说明并描述可见部分
7. **不确定就含糊**:"看似""可能是笔记本或平板"配对式;只对用户钉死的事斩钉截铁
8. **人物写可观察面**:体态、视线、神情、发肤、逐件服装(色+材质);年龄写人生阶段(少年/青年/中年/暮年)不写数字;脸转开或裁切就直说,不硬描
9. **物体写品类不写品牌**(银色笔记本、无反相机、两厢小车),用户点名品牌除外;摄影/设计词汇欢迎(浅景深、bokeh、逆光、负空间、投影)
10. **物理自洽**:影子背离光源、倒影对得上前景、相邻物体比例一致;用户要了物理上不可能的东西,按画面所示描述,让周围世界保持连贯

## 出处与边界

- 蒸馏自 Qwen/Qwen-Image-2.1-PE-T2I 与 PE-I2I 官方 system_prompt(2026-09-20 开源夜,原件为 Qwen 官方发布包 prompt_enhancer 的 system_prompt.txt)
- 本 skill = 会话内手工精修(可对话来回、带项目上下文);管线内全自动改写用服务器 PE 节点(注意其 T2I 固定输出英文、I2I 跟指令语言)
- 总纲与甲篇通用于各家生图模型;乙篇编辑细则为 Qwen2.1 编辑流定制,用于其他模型时保留思路、按该模型的编辑语法调整引用格式

## 配套工具

- 生成:ComfyArt `generate_image`(model `qwen-image-2.1-t2i.api.json`,prompt 用本 skill 炼制)
- 透明底:Qwen 直出的 PNG 不带有效 alpha,抠图走 `remove_background`(结果为真 RGBA)
