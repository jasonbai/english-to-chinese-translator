---
name: english-to-chinese-translator
description: |
  为雅思学习者设计的英译中精翻工具。逐段翻译英文文章，高亮Band 6+词汇，
  提供详细词汇拓展和语法解析。

  触发条件：
  - "翻译" + "雅思" / "IELTS"
  - "英文翻译成中文" + "词汇学习"/"语法解析"
  - "帮我分析这篇文章的雅思词汇"
  - "这个句子的语法结构是什么"

  不用于：纯翻译（无学习需求）、摘要生成、非英语文本。

argument-hint: [--level <band>] [--focus <area>] [--style <style>]
user-invocable: true
disable-model-invocation: false
---

# English-to-Chinese Translator for IELTS Learners

为雅思学习者设计的英译中精翻工具。逐段翻译英文文章，高亮 Band 6+ 词汇，提供词汇拓展和语法解析。

---

## 参数说明

| 参数 | 值 | 默认值 | 说明 |
|------|-----|--------|------|
| `--level` | `band6`, `band7`, `band8` | `band7` | 目标分数，影响词汇筛选严格度 |
| `--focus` | `vocabulary`, `grammar`, `both` | `both` | 学习重点 |
| `--style` | `detailed`, `concise`, `academic` | `detailed` | 输出风格 |

### 参数详解

#### `--level` 词汇分级

- **band6**: 高亮 Band 6+ 词汇（包含部分高级词汇），语法解释更基础
- **band7**: 仅高亮 Band 7+ 词汇（默认），平衡的语法分析
- **band8**: 仅高亮 Band 8+ 词汇（最严格），深度语法解析

#### `--focus` 学习重点

- **vocabulary**: 扩展词汇部分，简化语法（1-2点）
- **grammar**: 扩展语法部分（5+点），简化词汇
- **both**: 平衡展示（默认）

#### `--style` 输出风格

- **detailed**: 完整格式，多例句，详细分析（默认）
- **concise**: 精简格式，表格化词汇，1-2语法点
- **academic**: 学术风格，术语化，深度分析

---

## 工作流程（三步精简法）

```
┌─────────────────────────────────────────────────────────────┐
│  Step 1: 分析与翻译 (Analysis & Translation)                 │
│  - 识别文章主题、难度                                         │
│  - 提取 Band 6/7/8+ 候选词汇                                  │
│  - 逐段英中对照，标记高级词汇                                  │
├─────────────────────────────────────────────────────────────┤
│  Step 2: 词汇拓展 (Vocabulary Expansion)                     │
│  - 详细定义（中英）+ IPA发音 + 词性                            │
│  - 高分例句 + 中文翻译                                        │
│  - 搭配 + 同义词 + 雅思应用场景                                │
├─────────────────────────────────────────────────────────────┤
│  Step 3: 语法精讲 (Grammar Focus)                            │
│  - 2-3个核心语法结构解析                                      │
│  - 原文例句分析 + 仿写练习                                     │
└─────────────────────────────────────────────────────────────┘
```

---

## 长文本处理策略

当文本超过 **3000 词**时，采用分块并行处理：

### 分块原则
- 按段落边界分割，每块 2000-3000 词
- 保持段落完整性，不在句中断开
- 记录分块位置，便于后续合并

### 并行处理流程

```
Step 1: 文本分析 → 识别分块边界
Step 2: 启动 SubAgent 处理各分块
Step 3: 接缝检查（词汇一致性、术语统一）
Step 4: 合并输出 + 去重词汇表
```

### 接缝检查要点
- [ ] 词汇高亮标准一致
- [ ] 术语翻译统一（如 "sustainability" 全文统一译法）
- [ ] 语气风格连贯
- [ ] 无重复词汇条目

---

## 输出格式

### 文章概览

```markdown
# [文章标题] - 雅思精读

> **概览**：约 X 词 | Y 个 Band 6+ 词汇 | Z 个语法点 | 难度：Band X

---
```

### 翻译对照

```markdown
## 翻译对照

### 【Paragraph 1】

**English:**
The **unprecedented** pace of technological advancement has **precipitated** a **paradigm** shift...

**中文：**
技术进步前所未有的步伐已经引发了社会运作方式的范式转变...

---
```

### 词汇拓展

```markdown
## 词汇拓展 (Band 6+)

### 1. unprecedented (adj.)
- **释义**：空前的，前所未有的
- **发音**：/ʌnˈpresɪdentɪd/
- **例句**：The pandemic caused **unprecedented** disruption to global supply chains.
  > 疫情对全球供应链造成了前所未有的破坏。
- **搭配**：unprecedented scale, unprecedented times
- **同义词**：unparalleled, revolutionary
- **雅思应用**：Writing Task 2 讨论现代趋势时常用

---
```

### 语法精讲

```markdown
## 语法精讲

### 1. Present Perfect + Causative Verb

**结构**：Subject + has/have + [causative verb] + object

**原文例句**：
> "The unprecedented pace... has precipitated a paradigm shift..."

**解析**：现在完成时强调过去事件对现在的持续影响；"precipitate" 比 "caused" 更精确。

**仿写**：Social media ___ profound changes in interpersonal communication.
> 答案：has engendered / has precipitated

---
```

---

## 词汇分级标准

### Band 6+ 词汇特征（CEFR C1）
- 复杂含义和多重细微差别
- 高级动词、形容词和抽象名词
- 学术和专业术语
- IELTS Reading Passage 3、Writing Task 7+ 常用词

### 不应高亮的词汇
- 基础词汇（Band 4-5 / CEFR A2-B2）
- 基本学术词汇：analyze, approach, benefit, concept, create, data, develop, effect, factor, function, impact, issue, method, process, result, structure, theory
- 常见过渡词：however, therefore, moreover, nevertheless
- 基础动词：show, give, make, take, use, get, have

### Band 6+ 典型词汇示例

**动词**：
- **accelerate**, **alleviate**, **deteriorate**, **enhance**, **facilitate**
- **ameliorate**, **engender**, **exacerbate**, **mitigate**, **precipitate**

**名词**：
- **ambiguity**, **consensus**, **disparity**, **paradigm**, **phenomenon**
- **proliferation**, **sustainability**, **unprecedented**

**形容词**：
- **adverse**, **compelling**, **conducive**, **detrimental**, **inherent**
- **intricate**, **plausible**, **prevalent**, **resilient**, **viable**

---

## 质量检查清单

翻译完成后进行以下检查：

### 翻译质量
- [ ] 无"翻译腔"（不自然的中文表达）
- [ ] 准确传达原文含义和语气
- [ ] 长难句处理恰当

### 词汇高亮
- [ ] 仅高亮指定 Band 级别词汇
- [ ] 无遗漏的高级词汇
- [ ] 无误标的普通词汇

### 语法解析
- [ ] 解释清晰易懂
- [ ] 仿写练习有答案
- [ ] 与 IELTS 考试关联

### 格式规范
- [ ] 段落编号连续
- [ ] 词汇表无重复
- [ ] IPA 发音标注正确

---

## 参考文件

- `references/ielts-vocabulary-levels.md` - 词汇分级详细指南
- `references/examples.md` - 处理示例
- `references/subagent-prompt-template.md` - 长文本分块模板

---

## 示例输出

**输入**：
```
The unprecedented pace of technological advancement has precipitated a paradigm shift in how societies function. While this phenomenon manifests numerous benefits, it simultaneously exacerbates existing socioeconomic disparities.
```

**输出**：

```markdown
# 学术段落精读 - 雅思翻译

> **概览**：约 30 词 | 5 个 Band 6+ 词汇 | 2 个语法点 | 难度：Band 7

---

## 翻译对照

### 【Paragraph 1】

**English:**
The **unprecedented** pace of technological advancement has **precipitated** a **paradigm** shift in how societies function. While this **phenomenon** **manifests** numerous benefits, it simultaneously **exacerbates** existing socioeconomic disparities.

**中文：**
技术进步前所未有的步伐已经引发了社会运作方式的范式转变。虽然这一现象展现出诸多益处，但同时也加剧了现有的社会经济差异。

---

## 词汇拓展 (Band 6+)

### 1. unprecedented (adj.)
- **释义**：空前的，前所未有的
- **发音**：/ʌnˈpresɪdentɪd/
- **例句**：The pandemic caused **unprecedented** disruption to global supply chains.
  > 疫情对全球供应链造成了前所未有的破坏。
- **搭配**：unprecedented scale, unprecedented times, unprecedented growth
- **同义词**：unparalleled, revolutionary, ground-breaking
- **雅思应用**：Writing Task 2 讨论现代趋势时常用

### 2. precipitate (v.)
- **释义**：加速，促成（突然发生）
- **发音**：/prɪˈsɪpɪteɪt/
- **例句**：The economic crisis **precipitated** a wave of unemployment.
  > 经济危机加速了全国范围内的失业浪潮。
- **搭配**：precipitate a crisis, precipitate change, precipitate a collapse
- **同义词**：trigger, accelerate, hasten, catalyze
- **雅思应用**：Writing Task 2 因果关系论证

### 3. paradigm (n.)
- **释义**：范例，范式，思维模式
- **发音**：/ˈpærədaɪm/
- **例句**：The discovery challenged the prevailing scientific **paradigm**.
  > 这一发现挑战了当时主导的科学范式。
- **搭配**：paradigm shift, dominant paradigm, new paradigm
- **同义词**：model, pattern, framework
- **雅思应用**：Reading Passage 3 学术讨论

### 4. manifest (v.)
- **释义**：显示，表明，显现
- **发音**：/ˈmænɪfest/
- **例句**：The effects of climate change **manifest** differently across regions.
  > 气候变化的影响在不同地区表现出不同特征。
- **搭配**：manifest itself, manifest in, manifest as
- **同义词**：demonstrate, display, reveal
- **雅思应用**：替代 basic "show"

### 5. exacerbate (v.)
- **释义**：加剧，恶化
- **发音**：/ɪɡˈzæsəbeɪt/
- **例句**：Pollution **exacerbates** respiratory problems.
  > 污染加剧了呼吸系统问题。
- **搭配**：exacerbate a problem, exacerbate tensions
- **同义词**：aggravate, worsen, intensify
- **雅思应用**：Problem-solution essays

---

## 语法精讲

### 1. Present Perfect + Causative Verb

**结构**：Subject + has/have + [causative verb] + object

**原文例句**：
> "The unprecedented pace... **has precipitated** a paradigm shift..."

**解析**：
- 现在完成时强调过去事件对现在的持续影响
- "precipitate" 比 "caused" 更精确，暗示加速和促成

**仿写**：Social media ___ profound changes in interpersonal communication.
> 答案：has engendered / has precipitated

### 2. While + Contrasting Clause

**结构**：While [Clause A], [Clause B]

**原文例句**：
> "While this phenomenon manifests numerous benefits, it simultaneously exacerbates existing disparities."

**解析**：
- "While" 引导让步状语从句，展示对立观点
- 体现批判性思维，避免过于绝对化

**仿写**：While globalization has facilitated economic growth, it has simultaneously ___ traditional cultures.
> 答案：eroded / undermined
```

---

## 指导原则

1. **翻译质量**：准确、流畅、无翻译腔
2. **词汇筛选**：严格按 Band 级别，宁缺毋滥
3. **语法解析**：深入浅出，关联 IELTS 应用
4. **输出格式**：清晰层次，便于学习
5. **长文本**：分块处理，保持一致性
