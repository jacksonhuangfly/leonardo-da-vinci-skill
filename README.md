**English** | [简体中文](./README.zh-CN.md)

# Leonardo da Vinci.skill

A historically bounded lens for observation, visual reasoning, structure, motion, and creative practice.

[Examples](#examples) · [Installation](#installation) · [Method](#method) · [Sources](#sources) · [Maintenance](#maintenance) · [Credits](#credits-and-license)

Make a problem easier to inspect through sketches, comparisons, and careful observation. The skill offers contemporary applications inspired by Leonardo's methods without inventing his opinions about modern technology.

Responses default to English. An explicit request for Chinese switches to Simplified Chinese unless another variant is specified. The choice persists for the conversation unless limited to one answer or artifact, or changed later. Other explicitly requested languages are honored. A Chinese prompt, source, or README alone does not change the response language.

## Examples

These are hypothetical contemporary applications, not quotations or historical dialogue.

### Why can a smart team still misunderstand the problem?

Separate the team's label from the observed sequence. Record what a person actually does, compare a second case, and mark what remains inferred. A sketch or table can reveal a missing connection more clearly than another confident explanation.

### Why does a feature-complete product still feel incoherent?

Inspect how parts relate: hierarchy, transitions, main tasks, and attention. Completeness is not the same as coherence. Compare the visible structure with actual use, while preserving accessibility, content, and the user's intended style.

### Why sketch when AI can generate a polished image?

A sketch can reveal the assumptions used to construct an object. A generated image may also help explore variants, but a convincing rendering is not evidence that the object was observed or the mechanism works. Label observed, inferred, and proposed features separately.

### When does exploration become avoidance of finishing?

Ask what each iteration has taught and what the user has promised to deliver. A study can legitimately remain open; a deadline-bound product may need a decision. Choose a next comparison and a stopping condition rather than treating unfinishedness as proof of creativity.

## Installation

```bash
npx skills add justinhuangai/leonardo-da-vinci-skill
```

Try: `Use a Leonardo-inspired lens to identify what we need to observe before redesigning this workflow.`

To change languages explicitly: `Please answer in Simplified Chinese for the rest of this conversation.`

## Method

### Five working lenses

| Lens | Question | Route |
|---|---|---|
| Observation | What is visible, inferred, or still missing? | [Visual clarification](references/observation-and-visual-clarification.md) |
| Form and structure | How do the parts support the intended whole? | [Living design](references/form-structure-and-living-design.md) |
| Motion | What moves, changes, resists, or stalls? | [Mechanics and forces](references/motion-mechanics-and-natural-forces.md) |
| Experiment | What small comparison could change the decision? | [Prototyping](references/experiment-prototype-and-iteration.md) |
| Integrative craft | What is learned through making across disciplines? | [Workshop practice](references/workshop-expression-and-integrative-craft.md) |

### Eight heuristics

1. Observe before drawing a conclusion.
2. Externalize the relation that words leave unclear.
3. Study how parts interact, not just whether they exist.
4. Use natural analogies to suggest questions, not prove answers.
5. Examine transitions, scales, and changing viewpoints.
6. Distinguish a rendering, a prototype, and validated performance.
7. Connect disciplines through a shared method rather than collecting topics.
8. Preserve the difference between productive inquiry and postponed delivery.

[SKILL.md](SKILL.md) routes the task and defines evidence and language rules. These are working interpretations, not a verified list authored by Leonardo. Diagrams are optional when ordinary prose or examples serve the question better.

## Sources

- [Six research notes](references/research/README.md) cover workshop context, observation, anatomy and structure, motion, composition, and historical limits.
- [Three source records](references/sources/README.md) contain a Gutenberg catalog, a truncated Britannica article, and a Met essay attributed to Carmen Bambach.
- [Extraction framework](references/extraction-framework.md) separates historical support, interpretation, and modern applications.

The local archive has **no captured notebook passages or transcripts**. The Gutenberg page includes catalog metadata and an automated summary; it is not Leonardo's book text. References to specific codices, missing article sections, or uncaptured museum/library materials require separate verification. Two secondary captures cannot establish a complete intellectual biography.

## Repository layout

```text
leonardo-da-vinci-skill/
├── README.md                  # English overview
├── README.zh-CN.md            # Simplified Chinese overview
├── SKILL.md                   # Routing and shared rules
├── LICENSE
├── requirements.txt           # Optional capture dependencies
├── references/                # Operational routes and extraction framework
│   ├── research/              # Editorial notes
│   └── sources/               # Captures with evidence boundaries
├── scripts/                   # Capture, conversion, and checks
└── tests/                     # Tool regression tests
```

## Maintenance

Using the skill does not require the maintenance tools. Run checks from the repository root with Python 3.10 or later:

```bash
python3 scripts/check_links.py .
python3 scripts/check_sources_inventory.py .
python3 scripts/check_research_repetition.py references/research
python3 -m unittest discover -s tests -v
```

The checks and core tests use the standard library. Optional HTML capture tests also run when `beautifulsoup4` is installed. Install capture dependencies only when using the web/PDF tool:

```bash
python3 -m pip install -r requirements.txt
```

- `scripts/capture_web_source.py` captures source material. Its required `--language` records the original language (`en`, `zh-CN`, another tag, or `und` if undetermined); it does not translate it.
- `scripts/download_subtitles.sh` requires optional `yt-dlp`. It defaults to English, trying manual then automatic subtitles in that language. `--language zh-CN` explicitly selects Simplified Chinese tracks. It does not fall back across languages or to Traditional Chinese, and ignores external yt-dlp configurations.
- `scripts/srt_to_transcript.py` converts an existing SRT or VTT file to readable text. Command-line messages remain English.

Replace `VIDEO_URL` with the target URL:

```bash
bash scripts/download_subtitles.sh "VIDEO_URL" outputs/subtitles
bash scripts/download_subtitles.sh --language zh-CN "VIDEO_URL" outputs/subtitles
```

Checks validate structure, metadata, duplication, and tool behavior. They do not establish historical truth, source rights, or answer quality. Keep both README versions synchronized and preserve source limitations when extending the library.

## Credits and license

Maintained by Jackson Huang and assembled with [Nuwa.skill](https://github.com/alchaincyf/nuwa-skill). Thanks to Nuwa's authors and contributors for the tooling.

Original project content is released under the [MIT License](LICENSE). Referenced and excerpted third-party materials retain their own rights and terms; inclusion here does not relicense them under MIT.
