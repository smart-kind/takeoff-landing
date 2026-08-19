# PM Skills 原始资料库 — 起飞参考资料

> 来源：[deanpeters/Product-Manager-Skills](https://github.com/deanpeters/Product-Manager-Skills)
> 版本：v0.84（2026年8月10日）
> 协议：CC BY-NC-SA 4.0
> 总计：77 个 Skill

这是 Product-Manager-Skills 仓库的完整 skill 目录，作为"起飞"阶段的原始参考资料。
在使用本产品规划产品方案时，这些 skill 提供方法论支撑。

---

## 仓库信息

| 项目 | 内容 |
|------|------|
| **GitHub** | https://github.com/deanpeters/Product-Manager-Skills |
| **作者** | Dean Peters（Productside 创始人） |
| **版本** | v0.84 · August 10, 2026 |
| **Skill 总数** | 77 |
| **许可协议** | CC BY-NC-SA 4.0 |
| **支持平台** | Claude Code · Claude Desktop/Web · Codex · ChatGPT · Cursor · n8n · LangFlow · CrewAI · Gemini · 任何能读 Markdown 的 Agent |
| **Streamlit 试玩** | `pip install -r app/requirements.txt` → `streamlit run app/main.py` |

---

## Skill 三层体系

```
┌────────────────────────────────────────────────────────┐
│  WORKFLOW 技能 (19)                                    │
│  完整端到端 PM 流程，耗时几天到几周                    │
│  例：运行完整发现周期、撰写 PRD                        │
└────────────────────────────────────────────────────────┘
                       ↓ 编排
┌────────────────────────────────────────────────────────┐
│  INTERACTIVE 技能 (27)                                 │
│  引导式决策——3-5 个问题后给编号建议                     │
│  例：「哪个优先级框架适合这里？」                       │
└────────────────────────────────────────────────────────┘
                       ↓ 使用
┌────────────────────────────────────────────────────────┐
│  COMPONENT 技能 (24)                                   │
│  特定 PM 交付物模板，耗时 30-90 分钟                    │
│  例：用验收标准写用户故事                              │
└────────────────────────────────────────────────────────┘
```

---

## 完整 Skill 目录

### 战略定位

| Skill | 类型 | 说明 |
|-------|------|------|
| [problem-framing-canvas](https://github.com/deanpeters/Product-Manager-Skills/blob/main/skills/problem-framing-canvas/SKILL.md) | 交互式 | MITRE 的 Look Inward / Look Outward / Reframe 序列，防止团队解决错误的问题 |
| [positioning-statement](https://github.com/deanpeters/Product-Manager-Skills/blob/main/skills/positioning-statement/SKILL.md) | 组件 | Geoffrey Moore 的模板，定义服务对象、解决的问题、差异化 |
| [product-strategy-session](https://github.com/deanpeters/Product-Manager-Skills/blob/main/skills/product-strategy-session/SKILL.md) | 工作流 | 完整战略弧线：定位 → 问题框架 → 方案探索 → 路线图（2-4周） |
| [positioning-workshop](https://github.com/deanpeters/Product-Manager-Skills/blob/main/skills/positioning-workshop/SKILL.md) | 交互式 | — |
| [altitude-horizon-framework](https://github.com/deanpeters/Product-Manager-Skills/blob/main/skills/altitude-horizon-framework/SKILL.md) | 组件 | — |
| [recommendation-canvas](https://github.com/deanpeters/Product-Manager-Skills/blob/main/skills/recommendation-canvas/SKILL.md) | 组件 | — |

---

### 利益相关方

| Skill | 类型 | 说明 |
|-------|------|------|
| [stakeholder-identification](https://github.com/deanpeters/Product-Manager-Skills/blob/main/skills/stakeholder-identification/SKILL.md) | 组件 | 在所有接触之前映射每个利益相关方：广泛头脑风暴 → 盟友/受众/影响者 → R/P/D 标记 → 公平视角 → 缩小到优先目标 |
| [stakeholder-mapping](https://github.com/deanpeters/Product-Manager-Skills/blob/main/skills/stakeholder-mapping/SKILL.md) | 组件 | 运行两个互补网格（权力×兴趣用于参与策略；影响×权力用于提升谁的声音）并比较发现差距 |
| [stakeholder-engagement-advisor](https://github.com/deanpeters/Product-Manager-Skills/blob/main/skills/stakeholder-engagement-advisor/SKILL.md) | 交互式 | 每个利益相关方的参与计划：诊断其概况和上下文，然后提供定制的消息框架、媒介、节奏和命名的下一步行动 |
| [workshop-facilitation](https://github.com/deanpeters/Product-Manager-Skills/blob/main/skills/workshop-facilitation/SKILL.md) | 工作流 | 所有交互式技能的引导交互协议 |

---

### 客户发现与研究

| Skill | 类型 | 说明 |
|-------|------|------|
| [discovery-interview-prep](https://github.com/deanpeters/Product-Manager-Skills/blob/main/skills/discovery-interview-prep/SKILL.md) | 组件 | 基于研究目标规划 Mom Test 风格访谈 |
| [opportunity-solution-tree](https://github.com/deanpeters/Product-Manager-Skills/blob/main/skills/opportunity-solution-tree/SKILL.md) | 组件 | 生成机会和解决方案，然后推荐最佳概念验证先测试 |
| [discovery-process](https://github.com/deanpeters/Product-Manager-Skills/blob/main/skills/discovery-process/SKILL.md) | 工作流 | 完整发现周期：框架 → 研究 → 综合 → 验证（3-4周） |
| [customer-journey-map](https://github.com/deanpeters/Product-Manager-Skills/blob/main/skills/customer-journey-map/SKILL.md) | 组件 | — |
| [customer-journey-mapping-workshop](https://github.com/deanpeters/Product-Manager-Skills/blob/main/skills/customer-journey-mapping-workshop/SKILL.md) | 交互式 | — |
| [jobs-to-be-done](https://github.com/deanpeters/Product-Manager-Skills/blob/main/skills/jobs-to-be-done/SKILL.md) | 组件 | — |
| [lean-ux-canvas](https://github.com/deanpeters/Product-Manager-Skills/blob/main/skills/lean-ux-canvas/SKILL.md) | 组件 | — |

---

### 优先级与路线图

| Skill | 类型 | 说明 |
|-------|------|------|
| [prioritization-advisor](https://github.com/deanpeters/Product-Manager-Skills/blob/main/skills/prioritization-advisor/SKILL.md) | 交互式 | 问 3-5 个关于上下文的问题，然后推荐 RICE、ICE、Kano 或其他合适的替代方案 |
| [epic-breakdown-advisor](https://github.com/deanpeters/Product-Manager-Skills/blob/main/skills/epic-breakdown-advisor/SKILL.md) | 交互式 | 使用 Richard Lawrence 的 9 种模式拆分大型史诗 |
| [roadmap-planning](https://github.com/deanpeters/Product-Manager-Skills/blob/main/skills/roadmap-planning/SKILL.md) | 工作流 | 收集输入 → 定义史诗 → 优先级排序 → 排序 → 沟通（1-2周） |
| [epic-hypothesis](https://github.com/deanpeters/Product-Manager-Skills/blob/main/skills/epic-hypothesis/SKILL.md) | 组件 | — |
| [user-story-mapping-workshop](https://github.com/deanpeters/Product-Manager-Skills/blob/main/skills/user-story-mapping-workshop/SKILL.md) | 交互式 | — |
| [user-story-mapping](https://github.com/deanpeters/Product-Manager-Skills/blob/main/skills/user-story-mapping/SKILL.md) | 组件 | — |
| [feature-investment-advisor](https://github.com/deanpeters/Product-Manager-Skills/blob/main/skills/feature-investment-advisor/SKILL.md) | 交互式 | 使用收入影响、成本、ROI 和战略价值做构建/不构建推荐 |
| [derisk-measurement-advisor](https://github.com/deanpeters/Product-Manager-Skills/blob/main/skills/derisk-measurement-advisor/SKILL.md) | 交互式 | — |

---

### PM 交付物撰写

| Skill | 类型 | 说明 |
|-------|------|------|
| [prd-development](https://github.com/deanpeters/Product-Manager-Skills/blob/main/skills/prd-development/SKILL.md) | 工作流 | 结构化 PRD：问题 → 人物 → 方案 → 指标 → 故事（2-4天） |
| [user-story](https://github.com/deanpeters/Product-Manager-Skills/blob/main/skills/user-story/SKILL.md) | 组件 | Mike Cohn 格式 + Gherkin 验收标准，含反模式 |
| [user-story-splitting](https://github.com/deanpeters/Product-Manager-Skills/blob/main/skills/user-story-splitting/SKILL.md) | 组件 | — |
| [press-release](https://github.com/deanpeters/Product-Manager-Skills/blob/main/skills/press-release/SKILL.md) | 组件 | Amazon Working Backwards：在写规格之前明确产品愿景 |
| [storyboard](https://github.com/deanpeters/Product-Manager-Skills/blob/main/skills/storyboard/SKILL.md) | 组件 | — |
| [proto-persona](https://github.com/deanpeters/Product-Manager-Skills/blob/main/skills/proto-persona/SKILL.md) | 组件 | — |
| [problem-statement](https://github.com/deanpeters/Product-Manager-Skills/blob/main/skills/problem-statement/SKILL.md) | 组件 | — |

---

### 验证与实验

| Skill | 类型 | 说明 |
|-------|------|------|
| [pol-probe-advisor](https://github.com/deanpeters/Product-Manager-Skills/blob/main/skills/pol-probe-advisor/SKILL.md) | 交互式 | 根据你的假设和风险级别推荐运行哪种原型类型 |
| [pol-probe](https://github.com/deanpeters/Product-Manager-Skills/blob/main/skills/pol-probe/SKILL.md) | 组件 | 在构建之前记录轻量级验证实验的模板 |

---

### 商业健康与增长

| Skill | 类型 | 说明 |
|-------|------|------|
| [business-health-diagnostic](https://github.com/deanpeters/Product-Manager-Skills/blob/main/skills/business-health-diagnostic/SKILL.md) | 交互式 | 使用真实指标诊断 SaaS 在增长、留存、效率和资本方面的健康状况 |
| [organic-growth-advisor](https://github.com/deanpeters/Product-Manager-Skills/blob/main/skills/organic-growth-advisor/SKILL.md) | 交互式 | McKinsey 增长金字塔分诊：诊断你的约束是在新细分、地理、渠道还是产品 |
| [feature-investment-advisor](https://github.com/deanpeters/Product-Manager-Skills/blob/main/skills/feature-investment-advisor/SKILL.md) | 交互式 | 使用收入影响、成本、ROI 和战略价值做构建/不构建推荐 |
| [saas-economics-efficiency-metrics](https://github.com/deanpeters/Product-Manager-Skills/blob/main/skills/saas-economics-efficiency-metrics/SKILL.md) | 组件 | — |
| [saas-revenue-growth-metrics](https://github.com/deanpeters/Product-Manager-Skills/blob/main/skills/saas-revenue-growth-metrics/SKILL.md) | 组件 | — |
| [finance-based-pricing-advisor](https://github.com/deanpeters/Product-Manager-Skills/blob/main/skills/finance-based-pricing-advisor/SKILL.md) | 交互式 | — |
| [finance-metrics-quickref](https://github.com/deanpeters/Product-Manager-Skills/blob/main/skills/finance-metrics-quickref/SKILL.md) | 组件 | — |
| [tam-sam-som-calculator](https://github.com/deanpeters/Product-Manager-Skills/blob/main/skills/tam-sam-som-calculator/SKILL.md) | 交互式 | 三种市场估算方式：自己的数字、引导式访谈、或自下而上自主研究 |
| [acquisition-channel-advisor](https://github.com/deanpeters/Product-Manager-Skills/blob/main/skills/acquisition-channel-advisor/SKILL.md) | 交互式 | — |

---

### 市场与竞争情报（14+ 技能套件）

| Skill | 类型 | 说明 |
|-------|------|------|
| [intel-discipline-advisor](https://github.com/deanpeters/Product-Manager-Skills/blob/main/skills/intel-discipline-advisor/SKILL.md) | 交互式 | 从这里开始：将你桌子上的问题分诊到正确的情报学科、节奏和执行技能 |
| [intelligence-collection-disciplines](https://github.com/deanpeters/Product-Manager-Skills/blob/main/skills/intelligence-collection-disciplines/SKILL.md) | 组件 | 八种收集学科（OSINT → MASINT） |
| [autonomous-investigation](https://github.com/deanpeters/Product-Manager-Skills/blob/main/skills/autonomous-investigation/SKILL.md) | 工作流 | 无需你参与即可进行的研究协议。问题预算、搜索计划门控、每个声明的事实/推断/假设标签 |
| [competitive-analysis-process](https://github.com/deanpeters/Product-Manager-Skills/blob/main/skills/competitive-analysis-process/SKILL.md) | 工作流 | 六步总纲：格局 → 产品比较 → 客户需求 → 业务基线 → 定位 → 战略方向 |
| [market-landscape-scan](https://github.com/deanpeters/Product-Manager-Skills/blob/main/skills/market-landscape-scan/SKILL.md) | 组件 | — |
| [competitive-research-snapshot](https://github.com/deanpeters/Product-Manager-Skills/blob/main/skills/competitive-research-snapshot/SKILL.md) | 组件 | — |
| [competitive-intel-watch](https://github.com/deanpeters/Product-Manager-Skills/blob/main/skills/competitive-intel-watch/SKILL.md) | 组件 | — |
| [battle-card-builder](https://github.com/deanpeters/Product-Manager-Skills/blob/main/skills/battle-card-builder/SKILL.md) | 组件 | — |
| [swot-analysis](https://github.com/deanpeters/Product-Manager-Skills/blob/main/skills/swot-analysis/SKILL.md) | 组件 | — |
| [porters-five-forces](https://github.com/deanpeters/Product-Manager-Skills/blob/main/skills/porters-five-forces/SKILL.md) | 组件 | — |
| [ansoff-matrix](https://github.com/deanpeters/Product-Manager-Skills/blob/main/skills/ansoff-matrix/SKILL.md) | 组件 | — |
| [pestel-analysis](https://github.com/deanpeters/Product-Manager-Skills/blob/main/skills/pestel-analysis/SKILL.md) | 组件 | — |
| [pestel-delta-monitor](https://github.com/deanpeters/Product-Manager-Skills/blob/main/skills/pestel-delta-monitor/SKILL.md) | 组件 | — |
| [voice-of-customer-miner](https://github.com/deanpeters/Product-Manager-Skills/blob/main/skills/voice-of-customer-miner/SKILL.md) | 组件 | — |
| [pricing-packaging-tracker](https://github.com/deanpeters/Product-Manager-Skills/blob/main/skills/pricing-packaging-tracker/SKILL.md) | 组件 | — |
| [company-intel](https://github.com/deanpeters/Product-Manager-Skills/blob/main/skills/company-intel/SKILL.md) | 组件 | — |
| [company-research](https://github.com/deanpeters/Product-Manager-Skills/blob/main/skills/company-research/SKILL.md) | 组件 | — |

---

### 产品生命周期与退市

| Skill | 类型 | 说明 |
|-------|------|------|
| [lifecycle-play-advisor](https://github.com/deanpeters/Product-Manager-Skills/blob/main/skills/lifecycle-play-advisor/SKILL.md) | 交互式 | 当产品停止增长时从这里开始：七个过渡问题确定阶段，然后选择策略——扩展、替换或退市 |
| [product-lifecycle-plays](https://github.com/deanpeters/Product-Manager-Skills/blob/main/skills/product-lifecycle-plays/SKILL.md) | 组件 | PLC 战略网格、七种替换危害、风险登记册的最后一列问：什么是 Plan B？ |
| [eol-process](https://github.com/deanpeters/Product-Manager-Skills/blob/main/skills/eol-process/SKILL.md) | 工作流 | 整个日落在六个阶段：决定 → 对齐 → 计划 → 准备 → 宣布 → 关闭，包括跳过的 EOL 后审查 |
| [eol-readiness-advisor](https://github.com/deanpeters/Product-Manager-Skills/blob/main/skills/eol-readiness-advisor/SKILL.md) | 交互式 | 是/否决策，它会告诉你等待 |
| [eol-stakeholder-sequence](https://github.com/deanpeters/Product-Manager-Skills/blob/main/skills/eol-stakeholder-sequence/SKILL.md) | 组件 | 法律在财务之前，财务在销售之前——顺序错了，公告后才会发现地雷 |
| [eol-checklist](https://github.com/deanpeters/Product-Manager-Skills/blob/main/skills/eol-checklist/SKILL.md) | 组件 | 分阶段门控，每个项目一个负责人 |
| [eol-internal-enablement](https://github.com/deanpeters/Product-Manager-Skills/blob/main/skills/eol-internal-enablement/SKILL.md) | 组件 | 你的团队在客户听到之前就准备好了 |
| [eol-message](https://github.com/deanpeters/Product-Manager-Skills/blob/main/skills/eol-message/SKILL.md) | 组件 | 升级：三条过渡路径，包括诚实的无替代情况 |

---

### 职业与领导力过渡

| Skill | 类型 | 说明 |
|-------|------|------|
| [director-readiness-advisor](https://github.com/deanpeters/Product-Manager-Skills/blob/main/skills/director-readiness-advisor/SKILL.md) | 交互式 | 指导 PM 通过 PM→总监过渡的四种情况：准备、面试、新入职、重新校准 |
| [vp-cpo-readiness-advisor](https://github.com/deanpeters/Product-Manager-Skills/blob/main/skills/vp-cpo-readiness-advisor/SKILL.md) | 交互式 | 指导总监通过 VP/CPO 过渡，包括评估角色后再接受的 CEO 面试框架 |
| [executive-onboarding-playbook](https://github.com/deanpeters/Product-Manager-Skills/blob/main/skills/executive-onboarding-playbook/SKILL.md) | 组件 | VP/CPO 过渡的 30-60-90 天诊断剧本 |
| [product-sense-interview-answer](https://github.com/deanpeters/Product-Manager-Skills/blob/main/skills/product-sense-interview-answer/SKILL.md) | 组件 | — |

---

### AI 产品工作

| Skill | 类型 | 说明 |
|-------|------|------|
| [ai-shaped-readiness-advisor](https://github.com/deanpeters/Product-Manager-Skills/blob/main/skills/ai-shaped-readiness-advisor/SKILL.md) | 交互式 | 评估你是自动化任务（AI-first）还是重新设计工作方式（AI-shaped），然后告诉先建立哪种能力 |
| [context-engineering-advisor](https://github.com/deanpeters/Product-Manager-Skills/blob/main/skills/context-engineering-advisor/SKILL.md) | 交互式 | 诊断上下文堆砌 vs 上下文工程，指导 AI 驱动产品的记忆架构 |
| [agent-orchestration-advisor](https://github.com/deanpeters/Product-Manager-Skills/blob/main/skills/agent-orchestration-advisor/SKILL.md) | 交互式 | 指导多 Agent 工作流设计跨越四个维度 |

---

### 工具类

| Skill | 类型 | 说明 |
|-------|------|------|
| [pm-skill-creator](https://github.com/deanpeters/Product-Manager-Skills/blob/main/skills/pm-skill-creator/SKILL.md) | 交互式 | 通过引导对话设计符合仓库规范的 skills |
| [skill-authoring-workflow](https://github.com/deanpeters/Product-Manager-Skills/blob/main/skills/skill-authoring-workflow/SKILL.md) | 组件 | — |
| [incoming-request-advisor](https://github.com/deanpeters/Product-Manager-Skills/blob/main/skills/incoming-request-advisor/SKILL.md) | 交互式 | 放入 Slack ping、邮件、指令或升级，获得结构化分解，分离字面请求和真正的工作任务 |

---

## 每个 Skill 的文件结构

| 章节 | 内容 |
|------|------|
| **Frontmatter** | name, description, type, intent, best_for, scenarios |
| **Purpose** | 这个技能做什么、什么时候使用 |
| **Input** | 你可以带来什么（含示例调用）——已有信息直接使用，不会重复问 |
| **Key Concepts** | 框架、定义、反模式——附带词汇解释 |
| **Application** | Agent（或人）可以遵循的逐步说明 |
| **Examples** | 展示好坏版本的真实案例 |
| **Common Pitfalls** | 命名的失败模式及其后果和修正方法 |
| **References** | 相关技能和外部框架引用 |

## 如何使用这些资料

这些 skill 是"起飞"产品的方法论原材料。最终用户不需要直接面对这 77 个 skill——
产品会在适当的时候替用户选择和使用合适的 skill。
