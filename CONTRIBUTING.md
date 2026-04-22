# Contributing to SkillsJars Spring AI Example

Thank you for your interest in contributing to the SkillsJars Spring AI Example project! This document guides you through the contribution process.

## Development Environment Setup

### 1. Clone the Repository

```bash
git clone https://github.com/zhijunio/skillsjars-example-spring-ai.git
cd skillsjars-example-spring-ai
```

### 2. Verify Environment

```bash
# Check Java version
java -version  # Requires Java 21+

# Check Maven
./mvnw --version  # Requires Maven 3.9+
```

### 3. Configure Environment Variables

```bash
export OPENAI_API_BASE_URL=https://api.openai.com/v1
export OPENAI_API_KEY=your-api-key-here
export OPENAI_API_MODEL=gpt-4o
```

## Development Workflow

### 1. Create a Branch

```bash
# Start from the latest main branch
git checkout main
git pull origin main

# Create a feature branch
git checkout -b feature/your-feature-name

# Or create a fix branch
git checkout -b fix/issue-description
```

### 2. Make Changes

- Follow the existing code style when writing code
- Add necessary comments for new features
- Ensure code compiles and tests pass

### 3. Commit Changes

```bash
# View changes
git status
git diff

# Stage changes
git add <file-name>

# Commit (follow commit message conventions)
git commit -m "type: descriptive message"
```

### Commit Message Conventions

Follow [Conventional Commits](https://www.conventionalcommits.org/) format:

| Type | Description |
|------|-------------|
| `feat` | New feature |
| `fix` | Bug fix |
| `docs` | Documentation update |
| `style` | Code formatting (no functional change) |
| `refactor` | Refactoring |
| `test` | Test-related changes |
| `chore` | Build/tool configuration |

**Examples:**
```
feat: add new PDF export skill
fix: resolve null pointer in logging advisor
docs: update README with security notes
refactor: simplify ChatClient configuration
```

### 4. Push and Create PR

```bash
# Push branch
git push origin feature/your-feature-name

# Create PR using gh CLI (recommended)
gh pr create --title "feat: your feature description" --body "Description of changes"

# Or create via GitHub web interface
```

## Pull Request Guidelines

### PR Title

- Briefly describe the changes
- Follow commit message conventions
- Example: `feat: add support for Azure OpenAI`

### PR Description

Use the following template:

```markdown
## Summary
Briefly describe the purpose of this PR

## Changes
- [ ] New feature X
- [ ] Fix for issue Y
- [ ] Documentation update Z

## Testing
- [ ] Unit tests added/updated
- [ ] Manual testing performed
- [ ] Existing tests pass

## Related Issue
Fixes #<issue-number>
```

### Review Process

1. Project maintainers will review the code
2. Changes may be requested to meet requirements
3. After approval, changes are merged to main branch

## Reporting Issues

### Bug Reports

Use [GitHub Issues](https://github.com/zhijunio/skillsjars-example-spring-ai/issues) and include:

- **Description**: Clear description of the problem
- **Reproduction Steps**: How to trigger the issue
- **Expected Behavior**: What should happen
- **Actual Behavior**: What actually happened
- **Environment**: Java version, OS, dependency versions

### Feature Requests

- Describe the use case for the feature
- Explain why this feature is needed
- Provide implementation ideas (optional)

## Code Style

### Java Coding Standards

- Follow [Google Java Style Guide](https://google.github.io/styleguide/javaguide.html)
- Use 4-space indentation
- Class names use PascalCase
- Method/variable names use camelCase
- Constants use UPPER_SNAKE_CASE

### Example Code

```java
/**
 * Custom logging Advisor for recording chat requests and responses.
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

## Testing Requirements

### Unit Tests

- New utility classes should include unit tests
- Use JUnit 5 and Mockito
- Maintain reasonable test coverage

### Running Tests

```bash
# Run all tests
./mvnw test

# Run specific test class
./mvnw test -Dtest=MyLoggingAdvisorTest

# Generate coverage report
./mvnw clean test jacoco:report
```

## Release Process

### Releasing a New Version

1. Update version in `pom.xml`
2. Update `CHANGELOG.md`
3. Create Git tag
4. Run Release workflow

### Version Naming

Follow [Semantic Versioning](https://semver.org/):

```
MAJOR.MINOR.PATCH
  ↑      ↑      ↑
  Major  Minor  Patch
  Change Feature Fix
```

## Code of Conduct

- Be professional and respectful
- Welcome different perspectives and experiences
- Focus on constructive feedback
- Help new developers

## License

By contributing code, you agree to license your contribution under the [Apache License 2.0](LICENSE).

## Contact

- GitHub Issues: [Ask questions or discuss](https://github.com/zhijunio/skillsjars-example-spring-ai/issues)
- Email: zhijun.lab@gmail.com

---

Thank you for contributing!
