<div align="center">

**智能 AI 面试官平台** - 基于大语言模型的简历分析和模拟面试系统

[![Java](https://img.shields.io/badge/Java-21-orange?logo=openjdk)](https://openjdk.org/)
[![Spring Boot](https://img.shields.io/badge/Spring%20Boot-4.0-green?logo=springboot)](https://spring.io/projects/spring-boot)
[![React](https://img.shields.io/badge/React-18.3-blue?logo=react)](https://react.dev/)
[![TypeScript](https://img.shields.io/badge/TypeScript-5.6-blue?logo=typescript)](https://www.typescriptlang.org/)
[![PostgreSQL](https://img.shields.io/badge/PostgreSQL-pgvector-336791?logo=postgresql)](https://www.postgresql.org/)

</div>

---

## 项目介绍

本项目是一个集成了简历分析、模拟面试（文字 + 语音）和知识库管理的智能面试辅助平台。系统利用大语言模型（LLM）、向量数据库和实时语音技术，为求职者和 HR 提供智能化的简历评估和面试练习服务。

### 简历管理模块

- **多格式解析**：支持 PDF、DOCX、DOC、TXT 等多种简历格式。
- **异步处理流**：基于 Redis Stream 实现异步简历分析，支持实时查看处理进度（待分析/分析中/已完成/失败）。
- **稳定性保障**：内置分析失败自动重试机制（最多 3 次）与基于内容哈希的重复检测。
- **分析报告导出**：支持将 AI 分析结果一键导出为结构化的 PDF 简历分析报告。

### 模拟面试模块

- **Skill 驱动出题**：内置 10+ 面试方向（Java 后端、阿里/字节/腾讯专项、前端、Python、算法、系统设计、测开、AI Agent 等），每个方向由 `SKILL.md` 定义考察范围、难度分布和参考知识库。
- **历史题目去重**：出题时自动排除已有会话中问过的题目，避免重复考察。
- **面试阶段时长联动**：总时长滑块拖动后，各阶段（自我介绍、技术考察、项目深挖、反问环节）按时比自动分配。
- **智能追问流**：支持配置多轮智能追问（默认 1 条），模拟多轮问答场景。
- **统一评估架构**：文字面试和语音面试共用同一套评估引擎（分批评估 + 结构化输出 + 二次汇总 + 降级兜底），评估结果可对比。
- **报告一键导出**：支持异步生成并导出详细的 PDF 模拟面试评估报告。
- **面试中心入口**：面试中心页整合文字面试和语音面试入口，支持继续面试和重新面试。

### 面试安排模块

- **邀请解析**：规则 + AI 双引擎，支持飞书/腾讯会议/Zoom 格式，自动提取公司、岗位、时间、会议链接
- **日历管理**：日/周/月视图 + 拖拽调整 + 列表视图
- **状态流转**：定时任务自动过期，手动标记待面试/已完成/已取消
- **面试提醒**：可配置提醒，避免错过面试

### 语音面试模块

实时语音对话面试，WebSocket + 千问3 语音模型（ASR/TTS/LLM 统一 API Key）：

- **实时流式对话**：句子级并发 TTS，边生成边合成边播放，首包延迟 200ms
- **服务端 VAD**：自动断句，实时字幕（含中间结果）
- **回声防护 + 手动提交**：避免 AI 语音被误录入
- **多轮上下文记忆 + 暂停/恢复**：超时自动暂停
- **Micrometer 埋点**：TTS/ASR 延迟、会话时长等指标

### 知识库管理模块

- **文档智能处理**：支持 PDF、DOCX、Markdown 等多种格式文档的自动上传、分块与异步向量化。
- **RAG 检索增强**：集成向量数据库，通过检索增强生成（RAG）提升 AI 问答的准确性与专业度。
- **流式响应交互**：基于 SSE（Server-Sent Events）技术实现打字机式流式响应。
- **智能问答对话**：支持基于知识库内容的智能问答，并提供直观的知识库统计信息。
- ## 效果展示

### 简历与面试

面试中心：

![面试中心](https://oss.javaguide.cn/xingqiu/pratical-project/interview-guide/page-interview-hub.png)

Skill 出题 + JD 解析：

![Skill 出题 + JD 解析](https://oss.javaguide.cn/xingqiu/pratical-project/interview-guide/page-skill-jd-parse.png)

简历库：

![简历库](https://oss.javaguide.cn/xingqiu/pratical-project/interview-guide/page-resume-history.png)

简历上传分析：

![简历上传分析](https://oss.javaguide.cn/xingqiu/pratical-project/interview-guide/page-resume-upload-analysis.png)

简历分析详情：

![简历分析详情](https://oss.javaguide.cn/xingqiu/pratical-project/interview-guide/page-resume-analysis-detail.png)

面试记录：

![面试记录](https://oss.javaguide.cn/xingqiu/pratical-project/interview-guide/page-interview-history.png)

面试详情：

![面试详情](https://oss.javaguide.cn/xingqiu/pratical-project/interview-guide/page-interview-detail.png)

模拟面试：

![模拟面试](https://oss.javaguide.cn/xingqiu/pratical-project/interview-guide/page-mock-interview.png)

面试安排

![面试安排](https://oss.javaguide.cn/xingqiu/pratical-project/interview-guide/page-interview-schedule-list.png)

### 知识库

知识库管理：

![知识库管理](https://oss.javaguide.cn/xingqiu/pratical-project/interview-guide/page-knowledge-base-management.png)

问答助手：

![问答助手](https://oss.javaguide.cn/xingqiu/pratical-project/interview-guide/page-qa-assistant.png)


## 快速开始

环境要求：


| 依赖    | 版本 | 必需 | 说明                                        |
| ------- | ---- | ---- | ------------------------------------------- |
| JDK     | 21+  | 是   | 开发语言                                    |
| Node.js | 18+  | 是   | 前端构建                                    |
| Docker  | -    | 推荐 | 一键启动依赖服务（PostgreSQL/Redis/RustFS） |

### 1. 配置环境变量

如果只是本地测试的话，你也可以将 key 填入 `application.yml` 中。不过，考虑安全还是建议通过环境变量注入，可以通过 `export` 设置。

### 2. 启动依赖服务（可选）

项目提供了 `docker-compose.dev.yml`，可一键启动 PostgreSQL、Redis、RustFS（S3 兼容存储）三个依赖：

```bash
# 启动依赖服务
docker compose -f docker-compose.dev.yml up -d

# 停止依赖服务
docker compose -f docker-compose.dev.yml down

# 停止并清除数据
docker compose -f docker-compose.dev.yml down -v
```

启动后默认账号：


| 服务          | 地址             | 账号          | 密码          |
| ------------- | ---------------- | ------------- | ------------- |
| PostgreSQL    | `localhost:5432` | `postgres`    | `123456`      |
| Redis         | `localhost:6379` | -             | -             |
| RustFS 控制台 | `localhost:9001` | `rustfsadmin` | `rustfsadmin` |

> **注意**：首次启动后需浏览器访问 [http://localhost:9001](http://localhost:9001) 登录 RustFS 控制台，手动创建名为 `interview-guide` 的 Bucket。如果本地已有 MinIO 或其他 S3 兼容存储，也可以直接使用，在 `application.yml` 中修改对应的连接配置即可。

### 3. 启动应用

**后端：**

```bash
./gradlew bootRun
```

后端服务启动于 `http://localhost:8080`

**前端：**

```bash
cd frontend
pnpm install
pnpm dev
```

前端服务启动于 `http://localhost:5173`

## Docker 快速部署

本项目提供了完整的 Docker 支持，可以一键启动所有服务（前后端、数据库、中间件）。

Docker Compose 编排了 6 个服务：PostgreSQL（pgvector）、Redis、MinIO（S3 兼容存储）、MinIO Bucket 初始化、Spring Boot 后端、React 前端（Nginx）。数据通过 Docker 命名卷持久化，`docker-compose down` 不会丢失数据。

### 1. 前置准备

- 安装 [Docker](https://www.docker.com/products/docker-desktop/) 和 Docker Compose
- 申请阿里云百炼 API Key（用于 AI 对话功能，申请地址：[https://bailian.console.aliyun.com/](https://bailian.console.aliyun.com/)）

### 2. 快速启动

在项目根目录下执行：

`.env.example` 中的 PostgreSQL、Redis、MinIO 已与 `docker-compose.yml` 对齐（数据库用户 `postgres` / 密码 `password`，MinIO `minioadmin` / `minioadmin`）。复制为 `.env` 后主要填写 `AI_BAILIAN_API_KEY`；若你曾在旧版本中使用过不同的库密码或对象存储密钥，请同步修改 `.env`，必要时重建 Postgres 卷以免旧数据与密码不一致。

```bash
# 1. 复制环境变量配置文件
cp .env.example .env

# 2. 编辑 .env 文件，填入 AI 配置
# vim .env
# 必填：AI_BAILIAN_API_KEY=your_key_here
# 可选：AI_MODEL=qwen-plus        # 默认值为 qwen-plus
#        # 也可以改为 qwen-max、qwen-long 等其他可用模型
#
# 多 LLM 提供商支持（可选）：
# APP_VOICE_INTERVIEW_LLM_PROVIDER=dashscope  # 默认使用 DashScope
#        # 也支持：minimax, openai, deepseek, lmstudio
#        # 如需使用其他提供商，请参考 .env.example 中的配置说明
#
# 面试参数配置（可选）：
# APP_INTERVIEW_FOLLOW_UP_COUNT=1         # 每个主问题生成追问数量（默认 1）
# APP_INTERVIEW_EVALUATION_BATCH_SIZE=8   # 回答评估分批大小（默认 8）

# 3. 构建并启动所有服务
docker-compose up -d --build
```

> **仅启动依赖服务**：如果只想本地开发调试（用 `./gradlew bootRun` 启动后端），可以只启动基础设施：`docker compose up -d postgres redis minio createbuckets`。将 `.env.example` 复制为 `.env` 并填写 `AI_BAILIAN_API_KEY` 即可，默认账号与 `docker-compose.yml` 一致。
