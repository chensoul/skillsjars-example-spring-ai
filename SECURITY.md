# Security Policy

## Reporting a Vulnerability

We take the security of this project seriously. If you discover any security vulnerabilities, please disclose them responsibly.

### How to Report

Please report security vulnerabilities through one of the following channels:

1. **GitHub Private Vulnerability Reporting** (Recommended)
   - Visit https://github.com/zhijunio/skillsjars-example-spring-ai/security/advisories
   - Click "Report a vulnerability"
   - Fill in the details

2. **Email**
   - Send an email to: zhijun.lab@gmail.com
   - Subject line: `[Security] Brief description`

### Information to Include

To help us better understand and resolve the vulnerability, please provide:

- Type and description of the vulnerability
- Complete reproduction steps
- Affected versions
- Potential exploitation methods
- Suggested fix (if available)

### Response Timeline

- **Initial Response**: 1-3 business days
- **Status Updates**: Weekly
- **Fix Target**: Based on severity
  - Critical: 24-72 hours
  - High: 1 week
  - Medium: 2 weeks
  - Low: Next regular release

### Disclosure Policy

- Please do not publicly disclose vulnerabilities before they are fixed
- We will publish a security advisory after the fix
- Reporters will be acknowledged in the security advisory (if willing)

## Current Security Status

### Known Issues

| CVE | Severity | Status | Fixed Version |
|-----|----------|--------|---------------|
| - | - | - | - |

### Security Dependencies

We use the following tools to ensure dependency security:

- **Maven Dependency Check**: Automatically scans for known vulnerabilities
- **Renovate**: Automatically updates dependencies to secure versions

## Security Best Practices

### Developer Guidelines

1. **API Key Management**
   - Never commit API keys to version control
   - Use environment variables or secure key management services
   - Rotate keys regularly

2. **Dependency Management**
   - Regularly update dependencies to the latest secure versions
   - Review dependency licenses
   - Avoid using unmaintained libraries

3. **Code Review**
   - All code changes must be reviewed
   - Use static analysis tools
   - Follow secure coding guidelines

4. **Logging and Monitoring**
   - Do not log sensitive information
   - Implement proper error handling
   - Monitor for anomalous behavior

### User Guidelines

1. **ShellTools Usage**
   - This project includes `ShellTools` for demonstration purposes
   - Disable in production or implement command whitelisting
   - Do not run in untrusted environments

2. **API Keys**
   - Use API keys with minimal permissions
   - Rotate keys regularly
   - Monitor for unusual API usage

## Version Support

| Version | Support Status | Security Update Support |
|---------|----------------|-------------------------|
| Latest | ✅ Active | ✅ |
| Previous | ✅ Active | ✅ |
| Older | ❌ End of Life | ❌ |

## Security Changelog

Security-related changes are documented in the Security section of [CHANGELOG.md](CHANGELOG.md).

## Contact

For security concerns, please contact:

- Email: zhijun.lab@gmail.com
- GitHub Security Advisories: https://github.com/zhijunio/skillsjars-example-spring-ai/security/advisories

---

Thank you for helping keep this project secure!
