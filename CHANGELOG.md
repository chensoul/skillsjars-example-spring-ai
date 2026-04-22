# 变更日志

本文件记录项目的所有重要变更。

格式基于 [Keep a Changelog](https://keepachangelog.com/)，遵循 [语义化版本](https://semver.org/)。

## [未发布]

### Added
- 初始版本
- SkillsJars PDF 技能集成
- Spring AI Agent Utils 集成
- 自定义 `MyLoggingAdvisor` 用于日志调试
- 交互式 CLI 界面
- `ShellTools` 和 `FileSystemTools` 支持
- Maven Central 发布工作流
- Apache 2.0 许可证

### Changed
- 更新 Java 版本从 17 到 21（与 `.sdkmanrc` 一致）
- 将 Maven Central 发布的 `autoPublish` 从 `true` 改为 `false`
- `MyLoggingAdvisor` 添加敏感信息脱敏功能
- 完善 README.md 文档

### Fixed
- 修复 Java 版本配置不一致问题
- 修复日志可能泄露敏感信息的安全问题
- 添加 `ShellTools` 安全警告注释

### Security
- 添加 API key、token 等敏感信息的日志脱敏
- 添加 `ShellTools` 安全使用说明
- 完善发布流程的权限控制

---

## 版本说明

### 版本编号规则

- **主版本号**：重大架构变更或不兼容的 API 修改
- **次版本号**：新功能，向后兼容
- **修订号**：Bug 修复和小改进

### 发布流程

1. 更新此文件
2. 更新 `pom.xml` 版本号
3. 创建 Git 标签
4. 运行 GitHub Actions Release 工作流

---

## 链接

- [GitHub Releases](https://github.com/zhijunio/skillsjars-example-spring-ai/releases)
- [Maven Central](https://central.sonatype.com/artifact/io.zhijun/skillsjars-example-spring-ai)
