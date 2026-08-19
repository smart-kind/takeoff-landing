# Takeoff & Landing — PRD v7

> 版本：v7 · 2026-08-18
> 主题：API 设计 + 系统接口规范
> 状态：迭代中

---

## 1-9. 之前的内容（略）

v1-v6 的内容保留在对应版本文件中。本版本聚焦 API 层设计。

---

## 10. API 设计

### 10.1 API 风格

- **RESTful**，JSON 响应
- **版本前缀**：`/api/v1/`
- **认证**：v1 无认证（开放使用），v1.1 加 JWT

### 10.2 核心 API

#### 项目管理

| 方法 | 路径 | 说明 |
|------|------|------|
| POST | `/api/v1/projects` | 创建项目 |
| GET | `/api/v1/projects` | 列出用户所有项目 |
| GET | `/api/v1/projects/{id}` | 获取项目详情 |
| PATCH | `/api/v1/projects/{id}` | 更新项目 |
| DELETE | `/api/v1/projects/{id}` | 删除项目 |

#### 阶段管理

| 方法 | 路径 | 说明 |
|------|------|------|
| GET | `/api/v1/projects/{id}/phases` | 获取项目所有阶段 |
| PATCH | `/api/v1/phases/{id}` | 更新阶段状态 |

#### 草稿管理

| 方法 | 路径 | 说明 |
|------|------|------|
| POST | `/api/v1/projects/{id}/drafts` | 创建草稿 |
| GET | `/api/v1/projects/{id}/drafts` | 获取项目所有草稿 |
| GET | `/api/v1/drafts/{id}` | 获取草稿详情 |
| PATCH | `/api/v1/drafts/{id}` | 更新草稿 |
| DELETE | `/api/v1/drafts/{id}` | 删除草稿 |

#### Skill 导航引擎

| 方法 | 路径 | 说明 |
|------|------|------|
| GET | `/api/v1/projects/{id}/recommendations` | 获取当前推荐 skill |
| POST | `/api/v1/projects/{id}/recommendations/refresh` | 重新计算推荐 |
| PATCH | `/api/v1/recommendations/{id}` | 标记推荐为完成/开始 |

#### 引导对话

| 方法 | 路径 | 说明 |
|------|------|------|
| POST | `/api/v1/projects/{id}/chat` | 发送对话消息 |
| GET | `/api/v1/projects/{id}/chat/history` | 获取对话历史 |

#### PRD 生成

| 方法 | 路径 | 说明 |
|------|------|------|
| POST | `/api/v1/projects/{id}/prd/generate` | 触发 PRD 生成 |
| GET | `/api/v1/projects/{id}/prd` | 获取当前 PRD |
| GET | `/api/v1/projects/{id}/prd/export` | 导出 PRD（Markdown/PDF） |

#### 落地指南

| 方法 | 路径 | 说明 |
|------|------|------|
| GET | `/api/v1/landing-guides/{region}` | 获取指定地区的落地指南 |
| GET | `/api/v1/landing-guides/{region}/checklist` | 获取落地检查清单 |
| POST | `/api/v1/landing-guides/progress` | 更新落地进度 |

### 10.3 关键 API 示例

#### 创建项目

```json
POST /api/v1/projects
{
  "name": "我的 AI 知识图谱工具",
  "description": "帮开发者快速构建个人知识图谱的工具",
  "stage": "takeoff"
}

Response 201:
{
  "id": "proj_abc123",
  "name": "我的 AI 知识图谱工具",
  "description": "帮开发者快速构建个人知识图谱的工具",
  "stage": "takeoff",
  "progress": 0,
  "current_step": "problem_definition",
  "created_at": "2026-08-18T00:00:00Z"
}
```

#### 获取推荐

```json
GET /api/v1/projects/proj_abc123/recommendations

Response 200:
{
  "recommendations": [
    {
      "id": "rec_001",
      "skill_name": "problem-framing-canvas",
      "priority": 1,
      "reason": "你已经有一个模糊想法，但还没有明确要解决谁的什么问题。这一步能帮你理清思路。",
      "status": "pending"
    },
    {
      "id": "rec_002",
      "skill_name": "discovery-interview-prep",
      "priority": 2,
      "reason": "在投入开发之前，先验证这个需求是否真实存在。准备 3-5 个访谈问题就够了。",
      "status": "pending"
    },
    {
      "id": "rec_003",
      "skill_name": "proto-persona",
      "priority": 3,
      "reason": "明确你的目标用户是谁。用 10 分钟就能画出一个原型人物。",
      "status": "pending"
    }
  ]
}
```

#### 发送对话消息

```json
POST /api/v1/projects/proj_abc123/chat
{
  "message": "给那些想做产品但不会规划的开发者用"
}

Response 200:
{
  "response": "很好！那他们最大的痛点是什么？想想你遇到过的具体场景。",
  "step": "question_2_of_5",
  "progress": "2/5",
  "auto_saved": true
}
```

### 10.4 WebSocket（实时对话）

可选方案：引导对话通过 WebSocket 实现流式响应。

```
WS /api/v1/projects/{id}/chat/stream

Client → Server: {"message": "..."}
Server → Client: {"chunk": "很好！那他们..."}
Server → Client: {"chunk": "...最大的痛点是什么？"}
Server → Client: {"done": true, "step": "question_2_of_5"}
```

---

## 11. 后续迭代方向

- v8：商业模式 + 增长策略
- v9：安全 + 隐私 + 合规
- v10：实施路线图 + 风险评估
