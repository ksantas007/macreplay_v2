# Contributing to MacReplay v2

Thank you for your interest in contributing to MacReplay v2! This document provides guidelines and information for contributors.

## 🤝 How to Contribute

### Reporting Issues

1. **Check existing issues** first to avoid duplicates
2. **Use the issue template** when creating new issues
3. **Provide detailed information**:
   - MacReplay version
   - Unraid version
   - Docker version
   - Steps to reproduce
   - Expected vs actual behavior
   - Relevant logs

### Suggesting Features

1. **Open a feature request** issue
2. **Describe the feature** clearly
3. **Explain the use case** and benefits
4. **Consider the scope** - should it be in core or a plugin?

### Contributing Code

1. **Fork the repository**
2. **Create a feature branch**: `git checkout -b feature/your-feature-name`
3. **Make your changes**
4. **Test thoroughly** (see Testing section)
5. **Follow code style** guidelines
6. **Write clear commit messages**
7. **Submit a pull request**

## 🛠️ Development Setup

### Prerequisites

- Python 3.11+
- Docker and Docker Compose
- Git
- Basic knowledge of Flask and web development

### Local Development

1. **Clone the repository:**
   ```bash
   git clone https://github.com/T4s3rF4c3/macreplay_v2.git
   cd macreplay_v2
   ```

2. **Create a virtual environment:**
   ```bash
   python -m venv venv
   source venv/bin/activate  # On Windows: venv\Scripts\activate
   ```

3. **Install dependencies:**
   ```bash
   pip install -r requirements.txt
   ```

4. **Run the application:**
   ```bash
   python app-docker.py
   ```

5. **Access the interface:**
   ```
   http://localhost:8001
   ```

### Docker Development

1. **Build the image:**
   ```bash
   docker build -t macreplay:dev -f Dockerfile-unraid .
   ```

2. **Run with docker-compose:**
   ```bash
   docker-compose -f docker-compose-unraid.yml up -d --build
   ```

## 📝 Code Style Guidelines

### Python Code

- **Follow PEP 8** for Python code style
- **Use meaningful variable names**
- **Add docstrings** for functions and classes
- **Keep functions small** and focused
- **Use type hints** where appropriate

### Frontend Code

- **Use consistent indentation** (2 spaces for HTML/CSS/JS)
- **Follow Bootstrap conventions** for styling
- **Keep JavaScript functions small** and well-documented
- **Use semantic HTML** elements

### Template Code

- **Use proper Jinja2 syntax**
- **Keep templates organized** and well-structured
- **Add comments** for complex template logic
- **Ensure proper escaping** for security

## 🧪 Testing

### Manual Testing

1. **Test basic functionality:**
   - Portal management (add, edit, delete)
   - Channel editor (filtering, editing, preview)
   - Dashboard (statistics, status)
   - Settings (configuration changes)

2. **Test edge cases:**
   - Invalid portal URLs
   - Network connectivity issues
   - Large numbers of channels
   - Duplicate channel scenarios

3. **Test Unraid deployment:**
   - Container builds successfully
   - Proper file permissions
   - Volume mounts work correctly
   - Health checks pass

### Testing Checklist

- [ ] All existing features still work
- [ ] New features work as expected
- [ ] No console errors in browser
- [ ] Docker container builds and runs
- [ ] Configuration persists across restarts
- [ ] Logs are properly generated
- [ ] Resource usage is reasonable

## 📋 Pull Request Guidelines

### Before Submitting

1. **Test your changes** thoroughly
2. **Update documentation** if needed
3. **Check for conflicts** with main branch
4. **Ensure code follows** style guidelines

### PR Description

Include in your pull request:

- **Clear description** of changes
- **Issue reference** if applicable
- **Testing performed**
- **Screenshots** for UI changes
- **Breaking changes** if any

### Review Process

1. **Automated checks** must pass
2. **Code review** by maintainers
3. **Testing verification**
4. **Documentation review**
5. **Approval and merge**

## 🏗️ Project Structure

```
macreplay_v2/
├── app-docker.py          # Main application
├── stb.py                 # STB proxy functionality
├── requirements.txt       # Python dependencies
├── Dockerfile-unraid      # Unraid-specific Dockerfile
├── docker-compose-unraid.yml  # Unraid Docker Compose
├── unraid-template.xml    # Unraid template
├── templates/             # Jinja2 templates
│   ├── base.html         # Base template
│   ├── dashboard.html    # Dashboard interface
│   ├── editor.html       # Channel editor
│   ├── portals.html      # Portal management
│   └── settings.html     # Settings interface
├── static/               # Static assets
│   └── style.css        # Custom styles
├── .gitignore           # Git ignore rules
├── LICENSE              # MIT license
├── README.md            # Main documentation
├── CHANGELOG.md         # Version history
└── CONTRIBUTING.md      # This file
```

## 🎯 Areas for Contribution

### High Priority

- **Performance optimization** for large channel lists
- **Additional IPTV portal support**
- **Enhanced EPG integration**
- **Mobile-responsive improvements**
- **Automated testing framework**

### Medium Priority

- **Plugin system** for extensibility
- **Backup/restore functionality**
- **Advanced filtering options**
- **Channel grouping features**
- **Statistics and analytics**

### Documentation

- **Wiki pages** for advanced usage
- **Video tutorials** for setup
- **API documentation**
- **Troubleshooting guides**
- **Best practices documentation**

## 📞 Getting Help

- **GitHub Issues**: For bugs and feature requests
- **GitHub Discussions**: For questions and general discussion
- **Code Review**: Ask for feedback on your contributions

## 📜 License

By contributing to MacReplay v2, you agree that your contributions will be licensed under the MIT License.

## 🙏 Recognition

Contributors will be recognized in:
- **CHANGELOG.md** for significant contributions
- **README.md** acknowledgments section
- **GitHub contributors** page

Thank you for helping make MacReplay v2 better! 🚀