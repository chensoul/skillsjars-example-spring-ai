# SkillsJars Spring AI Example

[![License](https://img.shields.io/badge/License-Apache%202.0-blue.svg)](LICENSE)
[![Java](https://img.shields.io/badge/Java-21-orange.svg)](https://adoptium.net/)
[![Spring Boot](https://img.shields.io/badge/Spring%20Boot-4.0.5-brightgreen.svg)](https://spring.io/projects/spring-boot)
[![Spring AI](https://img.shields.io/badge/Spring%20AI-2.0.0--M4-blue.svg)](https://spring.io/projects/spring-ai)

本项目演示了如何将 [SkillsJars](https://www.skillsjars.com) 与 [Spring AI Agent Utils](https://github.com/spring-ai-community/spring-ai-agent-utils) 集成，使 AI 代理能够通过依赖定义的方式使用各种 Agent Skills。

## 功能特性

- **SkillsJars 集成** - 通过 Maven 依赖快速集成预构建的 AI 技能
- **Spring AI 支持** - 基于 Spring AI 2.0 构建，支持 OpenAI 兼容 API
- **工具调用** - 支持 Shell 命令、文件系统操作、PDF 生成等技能
- **交互式 CLI** - 命令行交互界面，支持多轮对话
- **日志调试** - 自定义 Advisor 显示工具调用和响应详情

## 技术栈

| 组件 | 版本 |
|------|------|
| Java | 21 |
| Spring Boot | 4.0.5 |
| Spring AI | 2.0.0-M4 |
| spring-ai-agent-utils | 0.7.0 |
| SkillsJars PDF | 2026_02_25-3d59511 |

## 快速开始

### 前置要求

- JDK 21+
- Maven 3.9+
- OpenAI API Key 或兼容的 LLM API

### 配置环境变量

```bash
# macOS / Linux
export OPENAI_API_BASE_URL=https://api.openai.com/v1
export OPENAI_API_KEY=your-api-key-here
export OPENAI_API_MODEL=gpt-4o

# Windows (PowerShell)
$env:OPENAI_API_BASE_URL="https://api.openai.com/v1"
$env:OPENAI_API_KEY="your-api-key-here"
$env:OPENAI_API_MODEL="gpt-4o"
```

### 运行应用

```bash
./mvnw spring-boot:run
```

启动后，您将看到交互式提示：

```
I am your assistant.

> USER:
```

### 使用示例

输入自然语言命令与 AI 交互：

```
> USER: 使用 PDF 技能创建包含当前目录列表的 PDF 文件

> USER: 列出当前目录下的所有 Java 文件

> USER: 读取 pom.xml 的内容
```

## 项目结构

```
skillsjars-example-spring-ai/
├── src/main/java/org/springaicommunity/agent/
│   ├── Application.java              # 主入口和 CLI 运行器
│   └── MyLoggingAdvisor.java         # 自定义日志 Advisor
├── src/main/resources/
│   └── application.properties        # 应用配置
├── .github/workflows/
│   └── release.yml                   # Maven Central 发布工作流
├── LICENSE                           # Apache 2.0 许可证
├── pom.xml                           # Maven 构建配置
└── README.md                         # 项目文档
```

## 核心组件

### Application.java

主应用程序类，负责：

- 构建 `ChatClient` 并配置默认工具
- 注册 `SkillsTool`、`ShellTools`、`FileSystemTools`
- 启动交互式 CLI 循环

### MyLoggingAdvisor.java

自定义的 Spring AI Advisor，用于：

- 记录用户输入和助手响应
- 显示可用的工具列表
- 显示工具调用和响应（自动脱敏敏感信息）

### 配置说明

`application.properties` 配置项：

```properties
# 禁用 Web 模式，使用 CLI
spring.main.web-application-type=none

# OpenAI 配置（通过环境变量）
spring.ai.openai-sdk.base-url=${OPENAI_API_BASE_URL}
spring.ai.openai-sdk.api-key=${OPENAI_API_KEY}
spring.ai.openai-sdk.chat.options.model=${OPENAI_API_MODEL}

# SkillsJars 技能路径
agent.skills.paths=classpath:/META-INF/skills
```

## 添加新技能

1. 在 `pom.xml` 中添加 SkillsJars 依赖：

```xml
<dependency>
    <groupId>com.skillsjars</groupId>
    <artifactId>anthropics__skills__{skill-name}</artifactId>
    <version>{version}</version>
</dependency>
```

2. 技能将自动被 `SkillsTool` 发现和注册

## 发布到 Maven Central

项目配置了自动发布到 Maven Central 的工作流。

### 手动发布

```bash
./mvnw clean deploy -P release
```

### 使用 GitHub Actions

1. 进入 Actions → Release
2. 输入版本号（如 `0.1.0`）
3. 运行工作流

### 所需 Secrets

| Secret | 描述 |
|--------|------|
| `MAVEN_USERNAME` | Sonatype Central 用户名 |
| `MAVEN_PASSWORD` | Sonatype Central 密码 |
| `GPG_SECRET_KEY` | GPG 私钥 |
| `GPG_PASSPHRASE` | GPG 私钥密码 |

## 安全注意事项

> **重要**: 本项目包含用于演示的 `ShellTools`，允许执行任意 shell 命令。

- **生产环境**: 请勿直接使用 `ShellTools`，或实施命令白名单
- **API 密钥**: 始终使用环境变量，不要提交到版本控制
- **日志脱敏**: `MyLoggingAdvisor` 会自动过滤日志中的敏感信息

## 常见问题

### Q: 支持哪些 LLM 提供商？

A: 任何 OpenAI 兼容的 API 都支持，包括：
- OpenAI
- Azure OpenAI
- 本地模型（Ollama、vLLM 等）

### Q: 如何自定义日志级别？

A: 修改 `MyLoggingAdvisor` 的构建器配置：

```java
MyLoggingAdvisor.builder()
    .showSystemMessage(true)
    .showAvailableTools(true)
    .showUserText(true)
    .showAssistantText(true)
    .build()
```

### Q: 如何贡献代码？

A: 欢迎提交 Pull Request！请确保：
- 代码通过现有测试
- 遵循现有代码风格
- 更新相关文档

## 相关资源

- [Spring AI 官方文档](https://docs.spring.io/spring-ai/reference/)
- [Spring AI Agent Utils](https://github.com/spring-ai-community/spring-ai-agent-utils)
- [SkillsJars](https://www.skillsjars.com)
- [Anthropic Skills](https://github.com/anthropics/skills)

## 许可证

[Apache License 2.0](LICENSE)
