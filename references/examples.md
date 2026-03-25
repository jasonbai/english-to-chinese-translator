# Processing Examples

This document provides examples of how to process different types of texts.

---

## Example 1: Short Academic Text (Under 500 words)

### Input
```
The unprecedented pace of technological advancement has precipitated a paradigm shift in how societies function. While this phenomenon manifests numerous benefits, it simultaneously exacerbates existing socioeconomic disparities.
```

### Expected Output

```markdown
# 精读翻译 - 雅思学术段落

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

## Example 2: Medium-Length Text (500-1500 words)

### Processing Strategy

1. **Divide into logical sections** (2-3 paragraphs per section)
2. **Process each section** with full vocabulary list
3. **Maintain consistent terminology** across sections
4. **Consolidate vocabulary** at the end (remove duplicates)

### Output Structure

```markdown
# [文章标题] - 雅思精读

> **概览**：约 X 词 | Y 个 Band 6+ 词汇 | Z 个语法点 | 难度：Band X

---

## 第一部分：[Section Title]

### 【Paragraph 1】
[Translation pair]

### 【Paragraph 2】
[Translation pair]

---

### 词汇拓展（第一部分）
[2-3 key words from this section]

---

## 第二部分：[Section Title]

### 【Paragraph 3】
[Translation pair]

---

### 词汇拓展（第二部分）
[2-3 key words from this section]

---

## 全文词汇汇总

| 词汇 | 词性 | 释义 | 出现段落 |
|------|------|------|----------|
| unprecedented | adj. | 空前的 | P1 |
| precipitate | v. | 加速促成 | P1 |
| ... | ... | ... | ... |

---

## 语法精讲（精选3个）

### 1. [Grammar Point 1]
[Detailed explanation with examples]

### 2. [Grammar Point 2]
[Detailed explanation with examples]

### 3. [Grammar Point 3]
[Detailed explanation with examples]
```

---

## Example 3: Long Text (3000+ words) - Parallel Processing

### When to Use Parallel Processing

- Text exceeds 3000 words
- Contains 5+ distinct sections
- User specifies `--style detailed`

### Processing Strategy

```
┌─────────────────────────────────────────────────────────────┐
│  Step 1: Text Analysis & Chunking                           │
│  - Count words and identify section boundaries              │
│  - Split at natural paragraph breaks                        │
│  - Target: 2000-3000 words per chunk                        │
├─────────────────────────────────────────────────────────────┤
│  Step 2: Parallel Translation (SubAgents)                   │
│  - Launch separate agent for each chunk                     │
│  - Pass context: terminology list, style preferences        │
│  - Each agent: translate + identify vocabulary              │
├─────────────────────────────────────────────────────────────┤
│  Step 3: Seam Check & Merge                                 │
│  - Verify vocabulary highlighting consistency               │
│  - Check terminology uniformity                             │
│  - Merge with coherent structure                            │
├─────────────────────────────────────────────────────────────┤
│  Step 4: Final Consolidation                                │
│  - Deduplicate vocabulary list                              │
│  - Select top 3-5 grammar points                            │
│  - Generate summary                                         │
└─────────────────────────────────────────────────────────────┘
```

### Chunk Division Example

```
Original Text (4000 words):
├── Introduction (500 words) → Chunk 1
├── Section 1: Background (1000 words) → Chunk 1
├── Section 2: Analysis (1200 words) → Chunk 2
├── Section 3: Discussion (800 words) → Chunk 2
└── Conclusion (500 words) → Chunk 2
```

### SubAgent Prompt Template

See `subagent-prompt-template.md` for the complete template.

---

## Example 4: Parameter Variations

### `--level band6` (More vocabulary highlighted)
- Include Band 6+ vocabulary
- Simpler grammar explanations
- More basic collocations

### `--level band7` (Default)
- Only Band 7+ vocabulary
- Intermediate grammar analysis
- Academic collocations

### `--level band8` (Most selective)
- Only Band 8+ vocabulary
- Advanced grammar patterns
- Nuanced usage notes

### `--focus vocabulary`
- Extended vocabulary section
- More synonyms and antonyms
- Additional example sentences
- Simplified grammar section (1 point)

### `--focus grammar`
- Extended grammar section (5+ points)
- Detailed structural analysis
- More imitation exercises
- Simplified vocabulary section

### `--style concise`
- Minimal formatting
- Essential information only
- Table format for vocabulary
- 1-2 grammar points

### `--style detailed`
- Full formatting
- Extended examples
- Multiple collocations
- 5+ grammar points

### `--style academic`
- Formal language
- Linguistic terminology
- Comprehensive analysis
- References to linguistic research
