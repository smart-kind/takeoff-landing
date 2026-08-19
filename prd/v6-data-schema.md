# Takeoff & Landing — PRD v6

> 版本：v6 · 2026-08-19
> 主题：数据结构设计 + 数据库 Schema
> 状态：迭代中

---

## 1. 一句话定位

**Takeoff & Landing**：给非 PM 用户的"傻瓜式产品经理"平台——把模糊想法变成可执行方案（起飞），把写好的代码变成可访问的产品（落地）。

---

## 2-7. 之前版本核心内容（保留引用）

v1-v5 的内容保留在对应版本文件中。本版本聚焦数据结构设计。

---

## 8. 技术架构选型（v5 决策回顾）

| 层次 | 选型 |
|------|------|
| 前端 | Next.js 15 + TypeScript + Tailwind CSS + shadcn/ui |
| 后端 | FastAPI + Pydantic + SQLAlchemy |
| 存储 | SQLite（开发/小型）→ PostgreSQL（生产） |
| AI 层 | LiteLLM 抽象层 + Ollama 本地 + 云端备用 |
| 桌面版 | Tauri |

---

## 9. 数据结构设计

### 9.1 设计原则

| 原则 | 说明 |
|------|------|
| **项目为中心** | 所有数据围绕"项目"聚合，确保一致数据源 |
| **渐进式建模** | 起步用扁平结构，随功能迭代逐步规范化 |
| **可导出性** | 每个核心实体都能独立导出为 Markdown/JSON |
| **AI 友好** | 字段设计考虑 LLM 理解和生成，避免嵌套过深 |
| **版本化** | 关键内容（PRD、需求文档）保留版本历史 |

### 9.2 核心实体关系

```
┌──────────────┐
│    User      │ 1
│  (用户)       │
└──────┬───────┘
       │ has many
       ▼
┌──────────────┐ 1         n ┌──────────────┐
│   Project    │─────────────│   Step       │
│  (项目)       │             │  (步骤)       │
└──────┬───────┘             └──────────────┘
       │ has many                    │
       ▼                             │ has many
┌──────────────┐                     ▼
│   Artifact   │             ┌──────────────┐
│  (交付物)     │             │    Q&A       │
└──────┬───────┘             │  (问答记录)   │
       │ has many            └──────────────┘
       ▼
┌──────────────┐
│   Version    │
│  (版本历史)   │
└──────────────┘
```

### 9.3 数据字典

#### User（用户）

| 字段 | 类型 | 约束 | 说明 |
|------|------|------|------|
| id | UUID | PK | 用户唯一标识 |
| email | VARCHAR(255) | UNIQUE, NOT NULL | 登录邮箱 |
| password_hash | VARCHAR(255) | NOT NULL | bcrypt 哈希 |
| display_name | VARCHAR(100) | NULL | 显示名称 |
| created_at | TIMESTAMP | NOT NULL, DEFAULT NOW() | 注册时间 |
| updated_at | TIMESTAMP | NOT NULL, DEFAULT NOW() | 最后更新 |
| settings | JSONB | NULL | 用户偏好设置（语言、主题、LLM 配置等） |

#### Project（项目）

| 字段 | 类型 | 约束 | 说明 |
|------|------|------|------|
| id | UUID | PK | 项目唯一标识 |
| user_id | UUID | FK → User.id, NOT NULL | 项目所有者 |
| title | VARCHAR(255) | NOT NULL | 项目名称 |
| description | TEXT | NULL | 项目描述/一句话想法 |
| phase | VARCHAR(50) | NOT NULL, DEFAULT 'idea' | 当前阶段：idea / takeoff / landing / launched |
| target_market | VARCHAR(50) | NULL | 目标市场：china / global / both |
| status | VARCHAR(50) | NOT NULL, DEFAULT 'active' | active / archived / deleted |
| metadata | JSONB | NULL | 扩展字段（行业、技术栈、团队规模等） |
| created_at | TIMESTAMP | NOT NULL, DEFAULT NOW() | 创建时间 |
| updated_at | TIMESTAMP | NOT NULL, DEFAULT NOW() | 最后更新 |
| completed_at | TIMESTAMP | NULL | 项目完成时间 |

#### Step（步骤）

| 字段 | 类型 | 约束 | 说明 |
|------|------|------|------|
| id | UUID | PK | 步骤唯一标识 |
| project_id | UUID | FK → Project.id, NOT NULL | 所属项目 |
| skill_ref | VARCHAR(100) | NOT NULL | 对应的 skill 标识符（如 "problem-framing-canvas"） |
| step_number | INTEGER | NOT NULL | 在该项目中的顺序编号 |
| title | VARCHAR(255) | NOT NULL | 步骤标题（如"明确你要解决谁的什么问题"） |
| description | TEXT | NULL | 步骤说明 |
| status | VARCHAR(50) | NOT NULL, DEFAULT 'pending' | pending / in_progress / completed / skipped |
| priority | INTEGER | NOT NULL, DEFAULT 0 | 推荐优先级（0=当前推荐，1=下一步，2=再下一步） |
| started_at | TIMESTAMP | NULL | 开始时间 |
| completed_at | TIMESTAMP | NULL | 完成时间 |
| created_at | TIMESTAMP | NOT NULL, DEFAULT NOW() | 创建时间 |

#### Artifact（交付物）

| 字段 | 类型 | 约束 | 说明 |
|------|------|------|------|
| id | UUID | PK | 交付物唯一标识 |
| project_id | UUID | FK → Project.id, NOT NULL | 所属项目 |
| step_id | UUID | FK → Step.id, NULL | 关联步骤（可为空，如手动创建的草稿） |
| type | VARCHAR(50) | NOT NULL | 类型：prd / user_story / persona / journey / roadmap / note |
| title | VARCHAR(255) | NOT NULL | 交付物标题 |
| content | TEXT | NOT NULL | 交付物内容（Markdown 格式） |
| current_version | INTEGER | NOT NULL, DEFAULT 1 | 当前版本号 |
| created_at | TIMESTAMP | NOT NULL, DEFAULT NOW() | 创建时间 |
| updated_at | TIMESTAMP | NOT NULL, DEFAULT NOW() | 最后更新 |

#### ArtifactVersion（交付物版本历史）

| 字段 | 类型 | 约束 | 说明 |
|------|------|------|------|
| id | UUID | PK | 版本记录唯一标识 |
| artifact_id | UUID | FK → Artifact.id, NOT NULL | 所属交付物 |
| version | INTEGER | NOT NULL | 版本号 |
| content | TEXT | NOT NULL | 该版本的内容快照 |
| change_summary | VARCHAR(500) | NULL | 变更说明 |
| created_at | TIMESTAMP | NOT NULL, DEFAULT NOW() | 创建时间 |

#### Q&A（问答记录）

| 字段 | 类型 | 约束 | 说明 |
|------|------|------|------|
| id | UUID | PK | 问答记录唯一标识 |
| step_id | UUID | FK → Step.id, NOT NULL | 所属步骤 |
| question | TEXT | NOT NULL | 系统提问 |
| answer | TEXT | NOT NULL | 用户回答 |
| context | JSONB | NULL | 附加上下文（用于 LLM 生成） |
| created_at | TIMESTAMP | NOT NULL, DEFAULT NOW() | 创建时间 |

### 9.4 数据库 Schema（SQLAlchemy 风格 DDL）

#### SQLite（开发环境）

```sql
-- Users
CREATE TABLE users (
    id TEXT PRIMARY KEY,                          -- UUID
    email TEXT UNIQUE NOT NULL,
    password_hash TEXT NOT NULL,
    display_name TEXT,
    settings TEXT,                                 -- JSON
    created_at TEXT NOT NULL DEFAULT (datetime('now')),
    updated_at TEXT NOT NULL DEFAULT (datetime('now'))
);

-- Projects
CREATE TABLE projects (
    id TEXT PRIMARY KEY,                          -- UUID
    user_id TEXT NOT NULL REFERENCES users(id),
    title TEXT NOT NULL,
    description TEXT,
    phase TEXT NOT NULL DEFAULT 'idea'
        CHECK (phase IN ('idea', 'takeoff', 'landing', 'launched')),
    target_market TEXT CHECK (target_market IN ('china', 'global', 'both')),
    status TEXT NOT NULL DEFAULT 'active'
        CHECK (status IN ('active', 'archived', 'deleted')),
    metadata TEXT,                                 -- JSON
    created_at TEXT NOT NULL DEFAULT (datetime('now')),
    updated_at TEXT NOT NULL DEFAULT (datetime('now')),
    completed_at TEXT
);

-- Steps
CREATE TABLE steps (
    id TEXT PRIMARY KEY,                          -- UUID
    project_id TEXT NOT NULL REFERENCES projects(id),
    skill_ref TEXT NOT NULL,
    step_number INTEGER NOT NULL,
    title TEXT NOT NULL,
    description TEXT,
    status TEXT NOT NULL DEFAULT 'pending'
        CHECK (status IN ('pending', 'in_progress', 'completed', 'skipped')),
    priority INTEGER NOT NULL DEFAULT 0,
    started_at TEXT,
    completed_at TEXT,
    created_at TEXT NOT NULL DEFAULT (datetime('now')),
    UNIQUE(project_id, step_number)
);

-- Artifacts
CREATE TABLE artifacts (
    id TEXT PRIMARY KEY,                          -- UUID
    project_id TEXT NOT NULL REFERENCES projects(id),
    step_id TEXT REFERENCES steps(id),
    type TEXT NOT NULL
        CHECK (type IN ('prd', 'user_story', 'persona', 'journey', 'roadmap', 'note')),
    title TEXT NOT NULL,
    content TEXT NOT NULL,
    current_version INTEGER NOT NULL DEFAULT 1,
    created_at TEXT NOT NULL DEFAULT (datetime('now')),
    updated_at TEXT NOT NULL DEFAULT (datetime('now'))
);

-- Artifact Versions
CREATE TABLE artifact_versions (
    id TEXT PRIMARY KEY,                          -- UUID
    artifact_id TEXT NOT NULL REFERENCES artifacts(id),
    version INTEGER NOT NULL,
    content TEXT NOT NULL,
    change_summary TEXT,
    created_at TEXT NOT NULL DEFAULT (datetime('now')),
    UNIQUE(artifact_id, version)
);

-- Q&A Records
CREATE TABLE qa_records (
    id TEXT PRIMARY KEY,                          -- UUID
    step_id TEXT NOT NULL REFERENCES steps(id),
    question TEXT NOT NULL,
    answer TEXT NOT NULL,
    context TEXT,                                  -- JSON
    created_at TEXT NOT NULL DEFAULT (datetime('now'))
);

-- Indexes
CREATE INDEX idx_projects_user ON projects(user_id);
CREATE INDEX idx_steps_project ON steps(project_id);
CREATE INDEX idx_artifacts_project ON artifacts(project_id);
CREATE INDEX idx_artifacts_step ON artifacts(step_id);
CREATE INDEX idx_qa_step ON qa_records(step_id);
CREATE INDEX idx_artifact_versions_artifact ON artifact_versions(artifact_id);
```

#### PostgreSQL（生产环境差异）

PostgreSQL 与 SQLite 的差异主要在：

```sql
-- UUID 类型
ALTER TABLE users ALTER COLUMN id TYPE UUID USING id::uuid;
-- （所有表的 id 字段同理）

-- JSONB 替代 TEXT（用于 JSON 字段）
ALTER TABLE users ALTER COLUMN settings TYPE JSONB USING settings::jsonb;
ALTER TABLE projects ALTER COLUMN metadata TYPE JSONB USING metadata::jsonb;
ALTER TABLE qa_records ALTER COLUMN context TYPE JSONB USING context::jsonb;

-- 时间戳类型
ALTER TABLE users ALTER COLUMN created_at TYPE TIMESTAMPTZ USING created_at::timestamptz;
-- （所有时间字段同理）
```

### 9.5 核心查询模式

#### 导航引擎：获取项目当前推荐步骤

```sql
-- 获取项目当前状态下的推荐步骤（priority=0,1,2）
SELECT s.id, s.title, s.status, s.priority, s.skill_ref
FROM steps s
WHERE s.project_id = :project_id
  AND s.status IN ('pending', 'in_progress')
ORDER BY s.priority ASC, s.step_number ASC
LIMIT 3;
```

#### 获取项目完整进度

```sql
-- 项目各阶段完成度
SELECT
    s.skill_ref,
    s.title,
    s.status,
    s.step_number,
    a.type AS artifact_type,
    a.current_version
FROM steps s
LEFT JOIN artifacts a ON a.step_id = s.id
WHERE s.project_id = :project_id
ORDER BY s.step_number ASC;
```

#### 获取交付物历史

```sql
-- 获取 PRD 的完整版本历史
SELECT v.version, v.content, v.change_summary, v.created_at
FROM artifact_versions v
WHERE v.artifact_id = :artifact_id
ORDER BY v.version DESC;
```

### 9.6 数据流示例

```
用户创建项目
  ↓
INSERT INTO projects (id, user_id, title, description, phase='idea')
  ↓
系统分析状态 → 生成初始步骤
  ↓
INSERT INTO steps (project_id, skill_ref, step_number, title, priority)
  × N 条（如 3 条，priority=0,1,2）
  ↓
用户完成步骤 1
  ↓
UPDATE steps SET status='completed', completed_at=NOW() WHERE id=...
INSERT INTO qa_records (step_id, question, answer)
  ↓
系统更新推荐
  ↓
UPDATE steps SET priority=0 WHERE ...  -- 新的当前推荐
UPDATE steps SET priority=1 WHERE ...
  ↓
用户完成所有起飞步骤
  ↓
UPDATE projects SET phase='takeoff_complete'
生成 PRD 交付物
  ↓
INSERT INTO artifacts (project_id, step_id, type='prd', title, content)
INSERT INTO artifact_versions (artifact_id, version=1, content)
```

### 9.7 迁移策略

| 阶段 | 数据库 | 迁移方式 |
|------|--------|---------|
| 开发 | SQLite 单文件 | SQLAlchemy `sqlite:///takeoff.db` |
| Alpha 内测 | SQLite 单文件 | 同上，数据可导出 |
| 公测 | PostgreSQL | Alembic migration，从 SQLite 导出 → 导入 PG |
| 生产 | PostgreSQL | 标准 Alembic migration |

使用 **Alembic** 管理数据库迁移，确保 SQLite 和 PostgreSQL 的 schema 差异通过 migration script 统一管理。

---

## 10. 后续迭代方向

- v7：API 设计 + 系统接口规范
- v8：商业模式 + 增长策略
- v9：安全 + 隐私 + 合规设计
- v10：完整实施路线图 + 风险评估
