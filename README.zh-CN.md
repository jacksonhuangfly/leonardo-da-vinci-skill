[English](./README.md) | **简体中文**

# 达芬奇.skill

在历史证据的边界内，借助观察、视觉推理、结构、运动与创作实践分析问题。

[示例](#示例) · [安装](#安装) · [方法](#方法) · [来源](#来源) · [维护](#维护) · [致谢](#致谢与许可)

通过草图、对照与细致观察，让问题更容易检查。这个 Skill 提供受达芬奇方法启发的现代应用，不编造他对现代技术的意见。

回答默认使用英文。用户明确请求中文后切换为简体中文，除非指定其他中文变体。该选择在当前对话中持续有效；仅针对一次回答或某个产物的请求只在相应范围生效，之后也可明确切换。其他明确指定的语言同样受支持。仅用中文提问、阅读中文来源或打开本说明文档，不会自动改变回答语言。

## 示例

以下都是假设性的现代应用，不是原话或历史对话。

### 为什么聪明的团队仍可能误解问题？

把团队给出的标签与实际观察到的过程分开。记录一个人真实做了什么，与第二个案例对照，并标明哪些仍是推断。草图或表格有时比另一段自信的解释更容易暴露缺失的联系。

### 为什么产品功能齐全，却仍然缺乏整体感？

检查部件之间的关系：层级、过渡、主要任务与注意力。齐全不等于协调。将可见结构与真实使用对照，同时保留无障碍需求、必要内容和用户选定的风格。

### AI 能生成精致图像，为什么还要画草图？

草图可以暴露构造对象时使用的假设。生成图像也能帮助探索变体，但看起来可信，不等于对象确实被观察过，也不等于机制可行。分别标明观察到的、推断出的和提议新增的部分。

### 什么时候探索变成了逃避完成？

检查每次迭代学到了什么，以及用户承诺交付什么。一项研究可以合理地保持开放，有明确期限的产品则可能需要定案。选择下一项对照与停止条件，不把未完成本身当作创造力的证明。

## 安装

```bash
npx skills add justinhuangai/leonardo-da-vinci-skill
```

可以这样提问：`Use a Leonardo-inspired lens to identify what we need to observe before redesigning this workflow.`

需要切换语言时明确说：`请在接下来的对话中使用简体中文回答。`

## 方法

### 五种工作视角

| 视角 | 问题 | 路由 |
|---|---|---|
| 观察 | 什么是可见的、推断的，什么仍然缺失？ | [视觉澄清](references/observation-and-visual-clarification.md) |
| 形式与结构 | 各部分如何支持预期的整体？ | [整体设计](references/form-structure-and-living-design.md) |
| 运动 | 什么在运动、改变、受阻或停滞？ | [机械与力](references/motion-mechanics-and-natural-forces.md) |
| 实验 | 哪个小型对照可能改变判断？ | [原型](references/experiment-prototype-and-iteration.md) |
| 综合技艺 | 跨学科的制作过程让人学到了什么？ | [工坊实践](references/workshop-expression-and-integrative-craft.md) |

### 八条启发式

1. 得出结论前先观察。
2. 将语言中不清楚的关系显现出来。
3. 研究部件如何互动，而不只检查它们是否存在。
4. 用自然类比提出问题，不把类比当成证明。
5. 检查过渡、尺度与视角变化。
6. 区分效果图、原型和经过验证的性能。
7. 通过共用方法连接学科，而不只是收集兴趣。
8. 区分有产出的探究与拖延交付。

[SKILL.md](SKILL.md) 负责路由选择，并规定证据与语言规则。这些是工作性解读，不是经核实由达芬奇本人制定的清单。如果普通文字或例子更适合问题，就不必强行绘图。

## 来源

- [六篇研究笔记](references/research/README.md)：涵盖工坊背景、观察、解剖与结构、运动、构图和历史边界。
- [三条来源记录](references/sources/README.md)：包括一个 Gutenberg 目录页、一篇截断的 Britannica 文章，以及署名 Carmen Bambach 的大都会艺术博物馆文章。
- [提炼框架](references/extraction-framework.md)：区分历史依据、解释与现代应用。

本地资料**没有实际捕获的笔记原文，也没有逐字稿**。Gutenberg 页面包含目录元数据和自动生成的摘要，不是达芬奇的书籍正文。涉及具体手稿、文章缺失章节、未收录的博物馆或图书馆资料时，需要另行核实。两份二手文章捕获不能证明完整的思想传记。

## 仓库结构

```text
leonardo-da-vinci-skill/
├── README.md                  # 英文说明
├── README.zh-CN.md            # 简体中文说明
├── SKILL.md                   # 路由与共用规则
├── LICENSE
├── requirements.txt           # 可选采集依赖
├── references/                # 操作路由与提炼框架
│   ├── research/              # 编者研究笔记
│   └── sources/               # 标明证据边界的捕获材料
├── scripts/                   # 采集、转换与检查工具
└── tests/                     # 工具回归测试
```

## 维护

使用 Skill 本身不需要维护工具。以下检查在仓库根目录运行，要求 Python 3.10 或更高版本：

```bash
python3 scripts/check_links.py .
python3 scripts/check_sources_inventory.py .
python3 scripts/check_research_repetition.py references/research
python3 -m unittest discover -s tests -v
```

检查器和核心测试只依赖标准库；安装 `beautifulsoup4` 后还会运行可选的 HTML 采集测试。只有使用网页或 PDF 采集工具时才需要安装采集依赖：

```bash
python3 -m pip install -r requirements.txt
```

- `scripts/capture_web_source.py` 采集来源材料。必填的 `--language` 记录原文语言，可填 `en`、`zh-CN`、其他标签，无法确定时填 `und`；它不会翻译原文。
- `scripts/download_subtitles.sh` 需要可选的 `yt-dlp`。默认下载英文字幕，按人工字幕、自动字幕的顺序尝试。显式传入 `--language zh-CN` 才选择简体中文字幕；不会跨语言回退，也不会回退到繁体中文，并忽略外部 yt-dlp 配置。
- `scripts/srt_to_transcript.py` 将已有 SRT 或 VTT 文件转换为可读文本。命令行提示保持英文。

将 `VIDEO_URL` 替换为目标网址：

```bash
bash scripts/download_subtitles.sh "VIDEO_URL" outputs/subtitles
bash scripts/download_subtitles.sh --language zh-CN "VIDEO_URL" outputs/subtitles
```

这些检查验证文档结构、来源元数据、重复文本和工具行为，不能证明历史事实、来源权利或回答质量。修改时同步维护两版 README，扩充资料时保留来源限制。

## 致谢与许可

本仓库由 Jackson Huang 维护，使用 [Nuwa.skill](https://github.com/alchaincyf/nuwa-skill) 辅助整理。感谢 Nuwa 的作者与贡献者提供工具。

项目原创内容采用 [MIT License](LICENSE)。引用或收录的第三方材料保留各自的权利与条款，不因进入本仓库而改用 MIT 许可。
