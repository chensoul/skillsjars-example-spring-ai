# Changelog

All notable changes to this project will be documented in this file.

The format is based on [Keep a Changelog](https://keepachangelog.com/), and this project adheres to [Semantic Versioning](https://semver.org/).

## [Unreleased]

### Added
- Initial release
- SkillsJars PDF skill integration
- Spring AI Agent Utils integration
- Custom `MyLoggingAdvisor` for logging and debugging
- Interactive CLI interface
- `ShellTools` and `FileSystemTools` support
- Maven Central release workflow
- Apache 2.0 License

### Changed
- Updated Java version from 17 to 21 (to match `.sdkmanrc`)
- Changed Maven Central `autoPublish` from `true` to `false`
- Added sensitive data redaction in `MyLoggingAdvisor`
- Improved README.md documentation

### Fixed
- Fixed Java version configuration mismatch
- Fixed security issue where logs could leak sensitive information
- Added security warning comment for `ShellTools`

### Security
- Added log redaction for API keys, tokens, and other sensitive data
- Added security usage notes for `ShellTools`
- Improved permission control in release process

---

## Version Numbering

- **Major**: Breaking architectural changes or incompatible API modifications
- **Minor**: New features, backward compatible
- **Patch**: Bug fixes and minor improvements

## Release Process

1. Update this file
2. Update version in `pom.xml`
3. Create Git tag
4. Run GitHub Actions Release workflow

---

## Links

- [GitHub Releases](https://github.com/zhijunio/skillsjars-example-spring-ai/releases)
- [Maven Central](https://central.sonatype.com/artifact/io.zhijun/skillsjars-example-spring-ai)
