# English-to-Chinese Translator

一个专为雅思学习者设计的 Claude Code 技能，提供逐段对照的英译中翻译，并高亮标记 IELTS Band 6+ 高级词汇，同时提供全面的词汇拓展和学习材料。

## 功能介绍

这个技能帮助准备雅思考试的学习者深入理解复杂的英文文章，同时构建高级词汇储备和掌握复杂语法结构。它的目标受众是雅思目标分数 Band 6+ 的学习者。

**核心功能：**

- **逐段对照翻译** — 英文原文与中文翻译逐段对照展示
- **高级词汇高亮** — 仅标记 IELTS Band 6+ 级别的高级词汇（粗体或红色）
- **详尽词汇拓展** — 提供词性、定义、例句、发音、搭配、同义词和使用说明
- **高级学习材料** — 包含针对 Band 6+ 学习者的深度语法解析和学习策略
- **雅思专项指导** — 针对听说读写四项的 Band 7+ 备考建议

## 核心特点

**精准的词汇分层**
- 仅标记真正的 Band 6+ (CEFR C1) 级别词汇
- 区分学术/专业词汇与基础词汇
- 专注于在雅思阅读 Passage 3、写作高分范文和口语 Part 3 中常见的高频高级词汇

**学术级语法解析**
- 大学水平的语法深度分析
- 不仅解释"是什么"，更解释"为什么"和"何时用"
- 提供常见错误及避免方法

**产出性学习导向**
- 不只关注理解，更关注运用
- 提供将高级词汇应用到雅思写作和口语的策略
- 培养批判性思维和多角度分析能力

**零依赖**
- 纯文本技能，无需外部工具或库
- 可直接集成到 Claude Code 工作流

## 安装

对于 Claude Code 用户

将技能文件复制到你的 Claude Code 技能目录：

```bash
# 创建技能目录
mkdir -p ~/.claude/skills/english-to-chinese-translator

# 复制技能文件
cp SKILL.md ~/.claude/skills/english-to-chinese-translator/
```

或直接克隆此仓库：

```bash
git clone https://github.com/你的用户名/english-to-chinese-translator.git ~/.claude/skills/english-to-chinese-translator
```

然后在 Claude Code 中输入 `/english-to-chinese-translator` 即可使用。

## 使用方法

### 翻译英文文章

```
/english-to-chinese-translator

> "请帮我翻译这篇关于人工智能的文章，并标注高级词汇"
```

技能将：

1. 逐段翻译，展示英文原文和中文翻译
2. 高亮标记 IELTS Band 6+ 级别的词汇
3. 提供完整的词汇拓展（定义、例句、搭配等）
4. 解析相关的高级语法点
5. 提供针对性的雅思备考建议

### 词汇学习

```
/english-to-chinese-translator

> "这段文章中有哪些雅思 Band 7+ 词汇？帮我详细解析"
```

技能将：

- 提取并解析所有 Band 6+ 级别词汇
- 提供每个词汇的详细用法说明
- 给出真实语境下的例句
- 展示在雅思考试中的应用场景

### 写作提升

```
/english-to-chinese-translator

> "我想提升雅思写作分数，帮我分析这篇文章的高级词汇和语法结构"
```

技能将：

- 识别文章中的高分词汇和语法
- 解释如何在 Writing Task 2 中运用
- 提供高分句型和表达方式
- 给出具体的写作建议

## 词汇等级说明

**IELTS Band 6+ (CEFR C1) - 高级学术和专业词汇**

这类词汇是高级学习者需要掌握才能在雅思考试中获得高分的词汇：

- 具有复杂含义和多重细微差别的词汇
- 复杂的动词、形容词和抽象名词
- 学术和专业术语
- 常见于雅思阅读 Passage 3、写作高分范文和口语 Part 3 的词汇

**示例词汇：**
- **unprecedented** (空前的)
- **precipitate** (促成，加速)
- **paradigm** (范式)
- **manifest** (显示，表明)
- **exacerbate** (加剧，恶化)

**不会标记的词汇：**
- 常见词汇 (Band 4-5 / CEFR A2-B2)
- 基础学术词汇
- 日常用语

## 输出格式示例

### 翻译部分

```
【Paragraph 1】

English (Original):
The **unprecedented** pace of technological advancement has **precipitated** a **paradigm** shift in how societies function.

中文翻译：
技术进步前所未有的步伐已经引发了社会运作方式的范式转变。
```

### 词汇拓展部分

```
## 词汇拓展 (Vocabulary Expansion)

### IELTS Band 6+ Words (CEFR C1 - Advanced)

1. **unprecedented** (adj.)
   - 中文定义：从未发生过、没有先例的
   - English Definition: Never done or known before
   - Example: The pandemic caused unprecedented disruption to global supply chains.
     疫情对全球供应链造成了前所未有的破坏。
   - Pronunciation: /ʌnˈpresɪdentɪd/
   - Collocations: unprecedented scale, unprecedented times
   - Synonyms: unparalleled, novel, revolutionary
   - Usage Notes: 常用于雅思写作 Task 2 讨论现代趋势和挑战时
```

### 学习要点部分

```
## 学习要点 (Learning Points)

### 雅思高级语法重点

详细的语法规则解释、结构分析、使用场景和雅思应用示例...

### 高级学习策略

词汇内化策略、语法复杂度提升策略、批判性思维培养...

### 雅思高分备考建议

针对 Reading、Writing、Speaking、Listening 四项的 Band 7+ 策略...
```

## 设计理念

这个技能基于以下信念：

**精确比数量更重要** — 只标记真正的高级词汇，避免学习者被过多信息淹没。

**理解是为了应用** — 不仅帮助理解文章，更要让学习者能够在雅思写作和口语中主动运用这些词汇。

**批判性思维是高分关键** — 雅思 Band 7+ 不只需要语言能力，更需要展示多角度思考和分析的能力。

**学习需要挑战** — 提供大学水平的语法解析和学习策略，挑战学习者向更高水平迈进。

## 适用场景

- 雅思备考（目标 Band 6.5-8.0）
- 学术英语学习
- 高级词汇积累
- 复杂文本阅读理解
- 学术写作提升
- 批判性思维训练

## 系统要求

- Claude Code CLI
- 无需额外依赖或库

## 致谢

由 @Jasonbai 使用 Claude Code 创建。

专为雅思 Band 6+ 学习者设计，帮助他们突破语言瓶颈，达到更高水平。

## 许可证

MIT — 自由使用、修改和分享。

---

**开始使用：** 在 Claude Code 中输入 `/english-to-chinese-translator`，开始你的雅思高级词汇学习之旅！
