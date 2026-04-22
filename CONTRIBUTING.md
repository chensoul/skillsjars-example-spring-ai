# 贡献指南

感谢您对SkillsJars Spring AI Example 项目的关注！本文档将指导您如何为项目做出贡献。

## 开发环境设置

### 1. 克隆仓库

```bash
git clone https://github.com/zhijunio/skillsjars-example-spring-ai.git
cd skillsjars-example-spring-ai
```

### 2. 验证环境

```bash
# 检查 Java 版本
java -version  # 需要 Java 21+

# 检查 Maven
./mvnw --version  # 需要 Maven 3.9+
```

### 3. 配置环境变量

```bash
export OPENAI_API_BASE_URL=https://api.openai.com/v1
export OPENAI_API_KEY=your-api-key-here
export OPENAI_API_MODEL=gpt-4o
```

## 开发流程

### 1. 创建分支

```bash
# 基于最新 main 分支
git checkout main
git pull origin main

# 创建功能分支
git checkout -b feature/your-feature-name

# 或创建修复分支
git checkout -b fix/issue-description
```

### 2. 进行开发

- 编写代码时遵循现有代码风格
- 为新增功能添加必要的注释
- 确保代码通过编译和测试

### 3. 提交代码

```bash
# 查看变更
git status
git diff

# 添加变更
git add <file-name>

# 提交（遵循提交信息规范）
git commit -m "type: descriptive message"
```

### 提交信息规范

采用 [Conventional Commits](https://www.conventionalcommits.org/) 格式：

| 类型 | 描述 |
|------|------|
| `feat` | 新功能 |
| `fix` | Bug 修复 |
| `docs` | 文档更新 |
| `style` | 代码格式（不影响功能） |
| `refactor` | 重构 |
| `test` | 测试相关 |
| `chore` | 构建/工具配置 |

**示例：**
```
feat: add new PDF export skill
fix: resolve null pointer in logging advisor
docs: update README with security notes
refactor: simplify ChatClient configuration
```

### 4. 推送并创建 PR

```bash
# 推送分支
git push origin feature/your-feature-name

# 使用 gh CLI 创建 PR（推荐）
gh pr create --title "feat: your feature description" --body "Description of changes"

# 或访问 GitHub 网页创建
```

## Pull Request 指南

### PR 标题

- 简洁描述变更内容
- 遵循提交信息规范
- 示例：`feat: add support for Azure OpenAI`

### PR 描述

使用以下模板：

```markdown
## 变更摘要
简要描述此 PR 的目的

## 变更详情
- [ ] 新增功能 X
- [ ] 修复问题 Y
- [ ] 更新文档 Z

## 测试方法
- [ ] 已添加单元测试
- [ ] 已进行手动测试
- [ ] 现有测试通过

## 相关 Issue
Fixes #<issue-number>
```

### 审查流程

1. 项目维护者将审查代码
2. 可能需要修改以满足要求
3. 审查通过后合并到 main 分支

## 报告问题

### Bug 报告

使用 [GitHub Issues](https://github.com/zhijunio/skillsjars-example-spring-ai/issues)，包含：

- **问题描述**：清晰描述问题
- **复现步骤**：如何触发问题
- **预期行为**：应该发生什么
- **实际行为**：实际发生了什么
- **环境信息**：Java 版本、OS、依赖版本

### 功能建议

- 描述功能的使用场景
- 说明为什么需要这个功能
- 提供可能的实现思路（可选）

## 代码风格

### Java 编码规范

- 遵循 [Google Java Style Guide](https://google.github.io/styleguide/javaguide.html)
- 使用 4 空格缩进
- 类名使用 PascalCase
- 方法/变量使用 camelCase
- 常量使用 UPPER_SNAKE_CASE

### 示例代码

```java
/**
 * 自定义日志 Advisor，用于记录聊天请求和响应。
 */
public class MyLoggingAdvisor implements BaseAdvisor {

    private static final Pattern API_KEY_PATTERN = Pattern.compile("...");
    private static final String REDACTED_VALUE = "[REDACTED]";

    private final int order;

    @Override
    public int getOrder() {
        return this.order;
    }
}
```

## 测试要求

### 单元测试

- 新增工具类应包含单元测试
- 使用 JUnit 5 和 Mockito
- 测试覆盖率应合理

### 运行测试

```bash
# 运行所有测试
./mvnw test

# 运行特定测试类
./mvnw test -Dtest=MyLoggingAdvisorTest

# 生成覆盖率报告
./mvnw clean test jacoco:report
```

## 发布流程

### 发布新版本

1. 更新 `pom.xml` 版本号
2. 更新 `CHANGELOG.md`
3. 创建 Git 标签
4. 运行 Release 工作流

### 版本命名

遵循 [Semantic Versioning](https://semver.org/)：

```
主版本号。次版本号。修订号
  ↑        ↑        ↑
  重大变化  新功能   Bug 修复
```

## 行为准则

- 保持专业和尊重
- 欢迎不同观点和经验
- 专注于建设性反馈
- 帮助新手开发者

## 许可证

通过贡献代码，您同意根据 [Apache License 2.0](LICENSE) 授权您的贡献。

## 联系方式

- GitHub Issues: [提问或讨论](https://github.com/zhijunio/skillsjars-example-spring-ai/issues)
- Email: zhijun.lab@gmail.com

---

感谢您的贡献！
