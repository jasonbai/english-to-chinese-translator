# English-to-Chinese Translator

一个专为雅思学习者设计的 Claude Code 技能，提供逐段对照的英译中翻译，高亮标记 IELTS Band 6+ 高级词汇，并提供词汇拓展和语法解析。

## 功能介绍

**核心功能：**

- **逐段对照翻译** — 英文原文与中文翻译逐段对照展示
- **高级词汇高亮** — 仅标记 IELTS Band 6+ 级别的高级词汇（粗体）
- **详尽词汇拓展** — 提供词性、定义、例句、发音、搭配、同义词和雅思应用
- **语法精讲** — 2-3个核心语法结构解析，含仿写练习
- **参数化支持** — 支持自定义学习级别、重点和输出风格
- **长文本处理** — 自动分块并行处理 3000+ 词文章

## 目录结构

```
english-to-chinese-translator/
├── SKILL.md                          # 主技能文件
├── README.md                         # 使用说明
└── references/                       # 参考资料目录
    ├── ielts-vocabulary-levels.md    # IELTS词汇分级指南
    ├── examples.md                   # 处理示例
    └── subagent-prompt-template.md   # 长文本分块模板
```

## 安装

### 方法一：复制到技能目录

```bash
# 创建技能目录
mkdir -p ~/.claude/skills/english-to-chinese-translator

# 复制所有文件
cp -r ./* ~/.claude/skills/english-to-chinese-translator/
```

### 方法二：克隆仓库

```bash
git clone https://github.com/jasonbai/english-to-chinese-translator.git ~/.claude/skills/english-to-chinese-translator
```

## 使用方法

### 基本用法

```
/english-to-chinese-translator

> 请帮我翻译这篇关于人工智能的文章
```

### 参数化调用

```
/english-to-chinese-translator --level band7 --focus vocabulary --style detailed
```

## 参数说明

| 参数 | 值 | 默认值 | 说明 |
|------|-----|--------|------|
| `--level` | `band6`, `band7`, `band8` | `band7` | 目标分数，影响词汇筛选严格度 |
| `--focus` | `vocabulary`, `grammar`, `both` | `both` | 学习重点 |
| `--style` | `detailed`, `concise`, `academic` | `detailed` | 输出风格 |

### `--level` 词汇分级

- **band6**: 高亮 Band 6+ 词汇，语法解释更基础
- **band7**: 仅高亮 Band 7+ 词汇（默认）
- **band8**: 仅高亮 Band 8+ 词汇（最严格）

### `--focus` 学习重点

- **vocabulary**: 扩展词汇部分，简化语法
- **grammar**: 扩展语法部分，简化词汇
- **both**: 平衡展示（默认）

### `--style` 输出风格

- **detailed**: 完整格式，多例句（默认）
- **concise**: 精简格式，表格化词汇
- **academic**: 学术风格，术语化分析

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

## 长文本处理

当文本超过 **3000 词**时，自动采用分块并行处理：

1. **分块**：按段落边界分割，每块 2000-3000 词
2. **并行翻译**：启动 SubAgent 处理各分块
3. **接缝检查**：确保词汇高亮一致、术语翻译统一
4. **合并输出**：去重词汇表，保持整体结构

## 输出格式示例

### 文章概览

```markdown
# [文章标题] - 雅思精读

> **概览**：约 X 词 | Y 个 Band 6+ 词汇 | Z 个语法点 | 难度：Band X
```

### 翻译对照

```markdown
### 【Paragraph 1】

**English:**
The **unprecedented** pace of technological advancement has **precipitated** a **paradigm** shift...

**中文：**
技术进步前所未有的步伐已经引发了社会运作方式的范式转变...
```

### 词汇拓展

```markdown
### 1. unprecedented (adj.)
- **释义**：空前的，前所未有的
- **发音**：/ʌnˈpresɪdentɪd/
- **例句**：The pandemic caused **unprecedented** disruption to global supply chains.
  > 疫情对全球供应链造成了前所未有的破坏。
- **搭配**：unprecedented scale, unprecedented times
- **同义词**：unparalleled, revolutionary
- **雅思应用**：Writing Task 2 讨论现代趋势时常用
```

### 语法精讲

```markdown
### 1. Present Perfect + Causative Verb

**结构**：Subject + has/have + [causative verb] + object

**原文例句**：
> "The unprecedented pace... has precipitated a paradigm shift..."

**解析**：现在完成时强调过去事件对现在的持续影响

**仿写**：Social media ___ profound changes in interpersonal communication.
> 答案：has engendered / has precipitated
```

## 词汇等级说明

**IELTS Band 6+ (CEFR C1) - 高级学术和专业词汇**

- 具有复杂含义和多重细微差别的词汇
- 复杂的动词、形容词和抽象名词
- 学术和专业术语
- 常见于雅思阅读 Passage 3、写作高分范文和口语 Part 3 的词汇

**示例词汇：**
- **unprecedented** (空前的), **precipitate** (促成), **paradigm** (范式)
- **exacerbate** (加剧), **mitigate** (缓解), **engender** (导致)
- **ambiguous** (模糊的), **benign** (良性的), **viable** (可行的)

**不会标记的词汇：**
- 常见词汇 (Band 4-5)
- 基础学术词汇：analyze, approach, benefit, concept, data, effect, issue, result
- 常见过渡词：however, therefore, moreover, nevertheless

## 参考文件

| 文件 | 内容 |
|------|------|
| `references/ielts-vocabulary-levels.md` | Band 6/7/8 词汇分级标准、典型词汇列表、话题词汇、搭配模式 |
| `references/examples.md` | 短文/中文/长文处理示例、参数变化示例 |
| `references/subagent-prompt-template.md` | 长文本分块翻译的子代理指令模板 |

## 最佳实践

### 💡 推荐工作流：Obsidian + Claudian

与 **Obsidian** 笔记软件 + **Claudian** 插件搭配使用效果最佳！

**使用流程：**

1. 在 Obsidian 中保存想要学习的英文文章
2. 使用 Claudian 插件调用 `/english-to-chinese-translator` 技能
3. 技能自动生成包含翻译、词汇拓展、语法解析的学习文档
4. 利用 Obsidian 的标签、链接功能进行复习

**获取 Claudian：** [Claudian GitHub](https://github.com/YishenTu/claudian)

## 适用场景

- 雅思备考（目标 Band 6.5-8.0）
- 学术英语学习
- 高级词汇积累
- 复杂文本阅读理解
- 学术写作提升

## 系统要求

- Claude Code CLI
- 无需额外依赖

## 更新日志

### v2.0 (2026-03)
- ✨ 新增参数化支持
- ✨ 新增长文本分块并行处理（3000+ 词）
- ✨ 新增 references 参考文件目录
- 🔧 精简工作流为三步法，移除冗余的备考策略章节
- 🔧 优化输出格式，更清晰的视觉层次
- 📝 完善词汇分级标准和典型词汇列表

### v1.0
- 初始版本：逐段翻译、词汇高亮、语法解析

## 致谢

由 @Jasonbai 使用 Claude Code 创建。

专为雅思 Band 6+ 学习者设计，帮助他们突破语言瓶颈，达到更高水平。

## 许可证

MIT — 自由使用、修改和分享。

---

**开始使用：** 在 Claude Code 中输入 `/english-to-chinese-translator`，开始你的雅思高级词汇学习之旅！
