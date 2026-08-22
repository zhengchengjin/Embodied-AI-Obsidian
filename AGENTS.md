# Embodied AI Obsidian Project

## Purpose

Maintain a long-lived Chinese Obsidian knowledge base for embodied intelligence, robot learning, and robotics research.

## Authoritative location

This project directory is the only authoritative vault. Update files in this directory directly. Do not create or maintain a second copy of the vault elsewhere.

## Weekly workflow

1. Maintain two parallel views: recent papers from the latest 7–14 days, and the current field frontier/SOTA by task and benchmark. Start from `01-主题索引/领域前沿与 SOTA 总览.md` and `06-方法与资源/SOTA 跟踪与证据标准.md` before deciding whether a new result changes the field coordinate.
2. Use `06-方法与资源/会议与期刊来源清单.md` as the venue source registry. Every weekly run must check for material updates from the core robotics venues RSS, CoRL, ICRA, and IROS, then scan relevant papers from NeurIPS, ICML, ICLR, CVPR, ICCV, ECCV, AAAI, IJCAI, Humanoids, HRI, and the listed robotics journals when official proceedings or accepted-paper lists change.
3. Prefer recent papers in arXiv `cs.RO`, cross-checking `cs.AI`, `cs.CV`, `cs.LG`, official conference proceedings and accepted-paper pages, project pages, and official benchmark leaderboards. A newly released or newly accepted conference paper may be selected even when its arXiv version is older than 14 days; state why it is timely.
4. Select five papers using `06-方法与资源/论文筛选与评分标准.md`. Avoid arXiv IDs already covered in the previous four weekly digests. Do not create duplicate permanent notes for arXiv and conference versions of the same work.
5. Read the full paper sections covering method, main experiments, key ablations, limitations, and failure cases. If only the abstract is accessible, label the entry `摘要速览`.
6. Create or update one permanent note per paper in `03-论文` using `05-模板/论文笔记模板.md`. Record the official venue, year, track, peer-review status, proceedings/DOI, and whether the conference version differs from the preprint. Also record whether its strongest result is strictly comparable to the current frontier, including benchmark version, split, data, embodiment, sensors, and evaluation protocol.
7. Create the weekly synthesis in `02-周报`, including `来源扫描` and `领域坐标变化` sections. The source scan must state which arXiv categories, conference proceedings, accepted-paper lists, and benchmark pages were checked, including an explicit "no material update" when applicable.
8. Update `01-主题索引/领域前沿与 SOTA 总览.md` only when primary-source evidence changes a result, status, or important open gap; do not rotate entries merely because a paper is newer. Then update relevant MOCs in `01-主题索引`, concept notes in `04-概念`, and `06-方法与资源/阅读队列.md`.
9. Separate author claims, reported experimental facts, and editorial judgment. State preprint, peer-review, code, data, checkpoint, and independent reproduction status explicitly. Main-conference, workshop, demo, oral, spotlight, Best Paper, and finalist labels must be recorded accurately and must not substitute for evidence evaluation.
10. Report absolute metrics with baselines, real-robot evidence, failure modes, and limitations. Do not present simulation-only evidence as real-world validation. Never use an unqualified "state of the art" claim across different tasks, benchmark versions, data conditions, embodiments, or evaluation protocols.

## Editing rules

- Preserve unrelated user edits and Obsidian settings.
- Do not overwrite `.obsidian/workspace.json`, `.obsidian/core-plugins.json`, or other user interface state unless explicitly requested.
- Use Obsidian wikilinks for internal knowledge links and ordinary Markdown links for external sources.
- Keep YAML frontmatter compatible with existing notes.
- Do not download paper PDFs into the vault unless explicitly requested; link to primary sources instead.
- Before finishing, verify that new wikilinks resolve and that no duplicate arXiv ID was introduced.

## Main entry point

Start from `00-首页/首页.md`.
