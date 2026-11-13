# document-governance-skills

AI 编程项目**工程文档治理技能包**：1 个总指挥元技能 + 3 个角色专家子技能（1+3 结构）。

`document-governance` 元技能担任**总指挥（Orchestrator）**：接收任务 → 按意图分类 → 派发子技能 → 闭环验收，不亲自执行具体操作。三个角色专家是被调度者。

## 组成与分工

| 技能 | 角色 | 职责 |
|---|---|---|
| 工程文档治理元技能 | **总指挥** | 任务分类派发、复合任务编排、类型/分层/doc-class 争议裁定、验收闭环；持有核心理念（人机双重视角、三层记录模型、现状/规范强制区分） |
| 文档编写专家 | 执行者 | 23 个超详细专业模板（五条线）：PRD/REQ-SPEC/USER-STORY/PERSONA/UI-SPEC/BUSINESS-PROCESS/DESIGN/ADR/API-CONTRACT/DDD-DESIGN/DEV-STANDARDS/REVERSE-ANALYSIS/TEST-PLAN/TEST-REPORT/DEPLOY-GUIDE/RUNBOOK/CHANGELOG/ROADMAP/PROGRESS/RETRO/HANDOFF/PR-SUMMARY/TECH |
| 文档评审专家 | 质检者 | 交叉验证四维度 + 分类型评审清单（含 14 类扩展系列门禁速查）+ 严重度分级报告（只报告不修改） |
| 文档治理专家 | 秩序者 | 分类分层目录、命名、单/多文档拆分决策、生命周期、漂移控制 |

## 路由机制（总指挥如何派活）

- **按任务意图查表**：写/补充内容 → writer；评审/验证 → reviewer；组织/拆分/归档 → governor；类型选择/体系设计/理念争议 → 元技能裁定。
- **复合任务编排**：如"建立项目文档体系" = governor（定结构）→ writer（产出最小集）→ 元技能验收；"文档体检" = reviewer（验证）→ governor（处置）→ writer（修复）→ reviewer（复验）。
- **歧义兜底**：先结构后内容（governor 先行）；摇摆超一次由总指挥裁定。
- **闭环验收**：子技能返回后核对分层、追踪链、索引登记；有 Blocker/Major 则派 writer 修复后复验。

## 核心模型速览

- **三层记录模型**：过程层（PROGRESS/RETRO/HANDOFF/PR-SUMMARY，追加式）→ 项目层（PRD/DESIGN/ADR/ROADMAP/API-CONTRACT 等，维护式）→ 知识层（TECH，提炼式）。信息只向下沉淀，不向上污染。
- **五类核心 + TECH**：PRD / DESIGN / ADR / PROGRESS / RETRO + 知识笔记 TECH；辅以 PERSONA / RUNBOOK / ROADMAP + 14 类扩展专业模板（需求规格、用户故事、API 契约、UI 规格、业务流程、DDD 设计、开发规范、测试计划/报告、部署指南、变更日志、交接单、交付摘要、逆向分析）。
- **核心真值链**：REQ-SPEC（需求真值）→ PRD/USER-STORY（转译）→ API-CONTRACT/DESIGN（承载）→ TEST-PLAN/TEST-REPORT（验证）→ DEPLOY-GUIDE/RUNBOOK（运维）→ CHANGELOG/PR-SUMMARY（交付记录）→ TECH/ADR（沉淀）。同一信息只维护一处。
- **doc-class 强制区分**：每篇文档声明 `as-is`（现状，漂移即缺陷）/ `to-be`（规范）/ `history`（历史快照，如 ADR）。
- **成熟格式经验**：ADR 五种状态管理（proposed/accepted/rejected/deprecated/superseded）、Persona 四阶段用户旅程、Runbook「前提条件-步骤-验证-排障」四段式、arc42 + C4 十二章设计骨架、Roadmap 当前迭代/待办强制分离、Keep a Changelog、ORRI 逆向分析。
- **模板统一规范**：frontmatter（doc-type/layer/doc-class/status/owner）+ 职责头（产出者/受众/归档/真值源/质量门禁）+ 逐节填写指引与示例 + 红线自查 + 追踪链。

## 安装

本包是**技能束（4 个平级技能）**，不是单技能。技能的发现单元是「目录 + 目录内 SKILL.md」，本包包含 4 个这样的标准单元，**包根没有也不需要 SKILL.md**（README 即束级说明；再设根 SKILL.md 会与总指挥元技能形成双重入口与路由歧义）。

将 4 个技能目录作为**平级兄弟**安装到技能目录（如 OpenCode 的 `~/.local/share/opencode/skills/`）：

```
skills/
├── document-governance/    # 总指挥元技能（任务入口）
├── doc-writer/
├── doc-reviewer/
└── doc-governor/
```

注意：

- **不可整包拷贝**：把 `document-governance-skills/` 整个目录拷入技能目录，会因根目录无 SKILL.md 而导致 4 个技能全部不可发现。
- **必须保持平级关系**：子技能通过 `../document-governance/` 相对路径引用元技能的 references，拆散或改变层级会断链。

## 使用

任何文档任务先进总指挥 `document-governance/SKILL.md`，由它分类派发：

- 写文档 → `doc-writer/SKILL.md`（模板在 `doc-writer/templates/` 五条线）
- 评审/验证文档 → `doc-reviewer/SKILL.md`
- 组织/拆分/归档文档 → `doc-governor/SKILL.md`
- 类型选择/体系设计/理念争议 → 由元技能直接裁定

## 目录

```
document-governance/
├── SKILL.md                       # 总指挥：调度协议 + 核心理念 + 路由
└── references/
    ├── three-layer-model.md       # 三层记录模型
    ├── core-doc-types.md          # 类型标准 + 14 类扩展系列 + 核心真值链
    └── as-is-vs-to-be.md          # 现状/规范强制区分
doc-writer/
├── SKILL.md                       # 编写流程 + 23 类型要点速查（五条线）
├── references/format-guides.md    # ADR五状态/arc42-C4/Persona四阶段/Runbook四段式/Roadmap
└── templates/                     # 23 个超详细专业模板
    ├── product/                   # PRD REQ-SPEC USER-STORY PERSONA UI-SPEC BUSINESS-PROCESS
    ├── architecture/              # DESIGN ADR API-CONTRACT DDD-DESIGN DEV-STANDARDS REVERSE-ANALYSIS
    ├── delivery/                  # TEST-PLAN TEST-REPORT DEPLOY-GUIDE RUNBOOK CHANGELOG ROADMAP
    ├── process/                   # PROGRESS RETRO HANDOFF PR-SUMMARY
    └── knowledge/                 # TECH
doc-reviewer/
├── SKILL.md                       # 交叉验证四维度 + 严重度分级 + 报告格式
└── references/checklists.md       # 分类型评审清单 + 扩展系列门禁速查
doc-governor/
├── SKILL.md                       # 目录/命名/生命周期/漂移控制/反模式
└── references/decision-frameworks.md  # 拆分决策/目录模式/场景决策表
```
