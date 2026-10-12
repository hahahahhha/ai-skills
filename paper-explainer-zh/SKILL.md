---
name: paper-explainer-zh
description: Explain academic papers in Chinese, then translate them section by section with aligned English originals. Use when the user asks for a paper overview, accessible explanation, Chinese translation, bilingual close reading, or to continue translating the next batch. Do not use for ordinary summarization that does not involve a paper.
---

# 论文讲解与逐节翻译

Identify the paper and read the complete relevant source before writing. Prefer the paper file or page supplied by the user. Check visual pages when text extraction may have corrupted formulas, symbols, tables, captions, or reading order. Do not silently guess unreadable text.

## First response for a paper

Produce the following in order:

1. **约 300 字概述**：用约 300 个中文汉字概括研究背景、核心问题、方法、主要结果与结论。保持信息密度，不展开逐段细节。
2. **深入浅出的论文讲解**：分别讲清楚：
   - 发现了什么问题，以及已有方案为什么不够；
   - 提出了什么方法，用直观类比解释关键机制，再补充必要技术细节；
   - 实验设置和最终数据，明确模型、数据量、指标、基线与数值；
   - 作者得出的结论、适用边界和局限。
3. **第一批逐节翻译**：立即翻译最前面的 5 个翻译单元，不等待用户再次确认。

区分实测结果、模拟结果、性能投影和作者推断。不得把投影速度写成真实硬件端到端实测。

## 翻译单元

按论文顺序，以“具有独立正文的最小标题单元”为一个翻译单元：

- 摘要算一个单元；编号章节或小节算一个单元。
- 只有标题而没有独立正文的父级章节不单独计数，其标题保留在首个子节之前。
- 父级章节标题后的引导段落并入其第一个子节，避免遗漏或人为拆碎。
- 图题、表题、公式及其紧邻解释归入所在小节，不另计单元。
- 致谢和参考文献仅在用户要求时翻译；默认不计入批次。

每批严格处理连续 5 个翻译单元。批末列出本批已完成的标题以及下一批的起始标题。用户说“继续”“下一批”或类似表达时，只翻译紧接着的 5 个单元；不要重复约 300 字概述和整体讲解，除非用户明确要求。

## 中英对照格式

每个翻译单元使用以下结构：

```markdown
### 1. Abstract / 摘要

**原文**

完整英文原文。

**中文翻译**

对应的完整中文译文。
```

翻译部分不是概述：逐段完整翻译，不删减论证、限定词、实验条件、数字、引用、公式、项目符号、图表标题或脚注。保持原文段落对应关系；遇到公式和符号时保留原式，只翻译周围文字。术语首次出现时使用“中文（English / abbreviation）”，后续保持译名一致。

纠正 PDF 提取造成的断词和排版噪声，但不得改写作者含义。若视觉核验后仍无法辨认，保留位置并标注 `[原文辨识不清]`，不要编造。

## 表达要求

- 禁止 hedging：概述和讲解直接给出证据支持的判断，禁止用“或许可以说”“某种程度上”“似乎有一定”等模糊措辞软化或回避结论；证据不足时直接指出具体缺口。不得为语气坚定而夸大证据或删除原文限定，翻译不得额外添加原文没有的缓冲措辞。

- 讲解部分可以使用类比，但要明确类比对应的技术对象。
- 翻译部分忠实、自然、正式；不要加入讲解、评价或额外背景。
- 保留证据边界和不确定性，不把“接近”“估计”“可能”翻译成确定结论。
- 若论文信息不足以支持某项结论，明确说明缺少什么证据。
