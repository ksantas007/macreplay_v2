# Security Policy

## 🔒 Reporting Security Vulnerabilities

The MacReplay v2 team takes security seriously. We appreciate your efforts to responsibly disclose security vulnerabilities.

### How to Report

**DO NOT** create public GitHub issues for security vulnerabilities.

Instead, please report security vulnerabilities via:

1. **Email**: Send details to the repository maintainer (check GitHub profile)
2. **GitHub Security**: Use GitHub's private vulnerability reporting feature
3. **Encrypted Communication**: PGP encryption welcome for sensitive reports

### What to Include

Please include the following information in your report:

- **Description** of the vulnerability
- **Steps to reproduce** the issue
- **Potential impact** and severity assessment
- **Affected versions** of MacReplay v2
- **Suggested fix** if you have one
- **Your contact information** for follow-up

### Response Timeline

- **Initial Response**: Within 48 hours of report
- **Assessment**: Within 1 week of initial response
- **Fix Development**: Timeline depends on severity and complexity
- **Public Disclosure**: After fix is available and deployed

## 🛡️ Security Considerations

### Network Security

MacReplay v2 operates as a proxy service and handles network traffic:

- **Input Validation**: All user inputs are validated and sanitized
- **URL Filtering**: Portal URLs are validated before processing
- **Rate Limiting**: Built-in protection against abuse
- **Error Handling**: Secure error messages that don't leak information

### Docker Security

When deploying MacReplay v2 in Docker:

- **Non-Root User**: Container runs as non-root user (uid 99, gid 100)
- **Limited Privileges**: Container has minimal required permissions
- **Network Isolation**: Uses Docker networking for security
- **Volume Security**: Properly configured volume permissions

### Web Interface Security

The web interface includes several security measures:

- **CSRF Protection**: Built-in protection against CSRF attacks
- **XSS Prevention**: Template escaping and content sanitization
- **Input Validation**: Server-side validation of all form inputs
- **Secure Headers**: Appropriate HTTP security headers

### Configuration Security

- **Environment Variables**: Sensitive data via environment variables
- **File Permissions**: Proper file system permissions
- **Default Settings**: Secure default configurations
- **Access Control**: Role-based access where applicable

## 🔧 Security Best Practices

### For Users

1. **Keep Updated**: Always use the latest version
2. **Secure Network**: Run on trusted networks only
3. **Access Control**: Limit access to authorized users
4. **Monitor Logs**: Regular log review for suspicious activity
5. **Backup Security**: Secure your configuration backups

### For Developers

1. **Input Validation**: Validate and sanitize all inputs
2. **Output Encoding**: Properly encode outputs
3. **Authentication**: Use secure authentication methods
4. **Authorization**: Implement proper access controls
5. **Logging**: Log security events appropriately
6. **Dependencies**: Keep dependencies updated

### For Deployments

1. **Network Segmentation**: Isolate the service appropriately
2. **Firewall Rules**: Configure proper firewall rules
3. **SSL/TLS**: Use HTTPS when possible
4. **Monitoring**: Implement security monitoring
5. **Backup Strategy**: Secure backup and recovery procedures

## 🚨 Known Security Considerations

### IPTV Portal Access

- MacReplay v2 acts as a proxy to IPTV portals
- Users are responsible for the legality of accessed content
- Portal credentials are stored locally (not transmitted to third parties)
- Always use trusted and legal IPTV sources

### Network Exposure

- By default, the service binds to all interfaces
- Consider network-level access controls
- Use reverse proxy for additional security layers
- Monitor access logs for suspicious activity

### Data Privacy

- Channel data is cached locally for performance
- User configurations are stored locally
- No data is transmitted to external services (except portal APIs)
- Regular cleanup of cached data is recommended

## 🔄 Security Updates

### Update Policy

- **Critical Vulnerabilities**: Emergency releases within 24-48 hours
- **High Severity**: Releases within 1 week
- **Medium/Low Severity**: Regular release cycle
- **Security Advisories**: Published via GitHub Security Advisories

### Supported Versions

We provide security updates for:

| Version | Supported          |
| ------- | ------------------ |
| 2.x.x   | ✅ Yes             |
| 1.x.x   | ❌ No              |

### Notification Methods

Security updates are announced via:

- **GitHub Releases**: All releases include security information
- **Security Advisories**: For critical vulnerabilities
- **CHANGELOG.md**: Detailed security fix information
- **README.md**: Security-related configuration updates

## 🤝 Security Community

### Bug Bounty

Currently, MacReplay v2 does not have a formal bug bounty program, but we greatly appreciate responsible disclosure and will acknowledge contributors appropriately.

### Security Research

We welcome security research on MacReplay v2:

- **Responsible Disclosure**: Follow responsible disclosure practices
- **Testing Environment**: Use your own test instances
- **Scope**: Focus on the application itself, not infrastructure
- **Legal Compliance**: Ensure all testing is legal and authorized

### Contributing to Security

You can help improve MacReplay v2 security by:

- **Code Review**: Reviewing pull requests for security issues
- **Security Testing**: Testing new features for vulnerabilities
- **Documentation**: Improving security documentation
- **Best Practices**: Sharing security best practices

## 📞 Contact Information

For security-related matters:

- **Security Team**: Contact repository maintainers
- **GitHub Security**: Use GitHub's security reporting features
- **Community**: Security discussions in GitHub Discussions

## 📝 Security Checklist

Before deployment, ensure:

- [ ] Latest version installed
- [ ] Secure network configuration
- [ ] Proper access controls
- [ ] SSL/TLS configured (if applicable)
- [ ] Firewall rules in place
- [ ] Monitoring configured
- [ ] Backup procedures tested
- [ ] Incident response plan ready

Thank you for helping keep MacReplay v2 secure! 🔐