# Contributing to KadoWebTube

Thank you for your interest in contributing to KadoWebTube! This document provides guidelines and instructions for contributing to the project.

## 📋 Table of Contents
- [Code of Conduct](#code-of-conduct)
- [Getting Started](#getting-started)
- [Development Setup](#development-setup)
- [Contributing Process](#contributing-process)
- [Code Standards](#code-standards)
- [Testing](#testing)
- [Documentation](#documentation)
- [Issue Guidelines](#issue-guidelines)
- [Pull Request Guidelines](#pull-request-guidelines)

## 🤝 Code of Conduct

By participating in this project, you agree to abide by our Code of Conduct:

- **Be respectful**: Treat everyone with respect and kindness
- **Be inclusive**: Welcome newcomers and help them learn
- **Be collaborative**: Work together towards common goals
- **Be constructive**: Provide helpful feedback and suggestions
- **Be professional**: Maintain professionalism in all interactions

## 🚀 Getting Started

### Prerequisites
- Node.js 16+ installed
- Git installed and configured
- Basic knowledge of JavaScript, Node.js, and Express.js
- Familiarity with PostgreSQL and Redis
- Understanding of REST API principles

### Development Setup

1. **Fork the repository**
   ```bash
   # Fork the repo on GitHub, then clone your fork
   git clone https://github.com/YOUR_USERNAME/kadowebtube-automation.git
   cd kadowebtube-automation
   ```

2. **Add upstream remote**
   ```bash
   git remote add upstream https://github.com/ORIGINAL_OWNER/kadowebtube-automation.git
   ```

3. **Install dependencies**
   ```bash
   npm install
   ```

4. **Setup environment**
   ```bash
   cp .env.example .env
   # Edit .env with your local configuration
   ```

5. **Setup database**
   ```bash
   npm run migrate
   npm run seed
   ```

6. **Start development server**
   ```bash
   npm run dev
   ```

## 🔄 Contributing Process

### 1. Create a Feature Branch
```bash
# Update your main branch
git checkout main
git pull upstream main

# Create a new feature branch
git checkout -b feature/your-feature-name
# or
git checkout -b fix/your-fix-name
```

### 2. Make Changes
- Write clean, maintainable code
- Follow existing code style and conventions
- Add tests for new functionality
- Update documentation as needed

### 3. Test Your Changes
```bash
# Run tests
npm test

# Run linting
npm run lint

# Check code formatting
npm run format:check
```

### 4. Commit Your Changes
```bash
# Add your changes
git add .

# Commit with a descriptive message
git commit -m "feat: add new campaign scheduling feature"

# Follow conventional commit format:
# feat: new feature
# fix: bug fix
# docs: documentation changes
# style: formatting changes
# refactor: code refactoring
# test: test additions/changes
# chore: maintenance tasks
```

### 5. Push and Create Pull Request
```bash
# Push to your fork
git push origin feature/your-feature-name

# Create pull request on GitHub
```

## 📏 Code Standards

### JavaScript Style Guide
- Use ES6+ features where appropriate
- Follow the existing code style (we use ESLint and Prettier)
- Use meaningful variable and function names
- Add JSDoc comments for functions and classes
- Keep functions small and focused

### Example Code Style
```javascript
/**
 * Creates a new campaign with the provided data
 * @param {Object} campaignData - The campaign data
 * @param {string} campaignData.name - Campaign name
 * @param {string} campaignData.targetUrl - Target YouTube URL
 * @param {number} campaignData.quantity - Number of engagements
 * @returns {Promise<Object>} Created campaign object
 */
async function createCampaign(campaignData) {
    const { name, targetUrl, quantity } = campaignData;
    
    // Validate input data
    if (!name || !targetUrl || !quantity) {
        throw new ValidationError('Missing required campaign data');
    }
    
    // Create campaign logic here
    const campaign = await Campaign.create(campaignData);
    
    return campaign;
}
```

### Database Standards
- Use descriptive table and column names
- Add proper indexes for performance
- Include foreign key constraints
- Add comments for complex queries

### API Standards
- Follow RESTful conventions
- Use consistent response formats
- Include proper HTTP status codes
- Add comprehensive error handling
- Document all endpoints

## 🧪 Testing

### Writing Tests
- Write unit tests for all new functions
- Include integration tests for API endpoints
- Add end-to-end tests for critical user flows
- Maintain test coverage above 80%

### Running Tests
```bash
# Run all tests
npm test

# Run tests in watch mode
npm run test:watch

# Run tests with coverage
npm run test:coverage

# Run specific test file
npm test -- tests/campaign.test.js
```

### Test Structure
```javascript
describe('Campaign Service', () => {
    describe('createCampaign', () => {
        it('should create a campaign with valid data', async () => {
            // Arrange
            const campaignData = {
                name: 'Test Campaign',
                targetUrl: 'https://youtube.com/watch?v=test',
                quantity: 1000
            };
            
            // Act
            const result = await createCampaign(campaignData);
            
            // Assert
            expect(result).toBeDefined();
            expect(result.name).toBe(campaignData.name);
        });
    });
});
```

## 📚 Documentation

### Code Documentation
- Add JSDoc comments for all public functions
- Include examples in documentation
- Keep README files up to date
- Document API endpoints thoroughly

### API Documentation
- Use consistent format for endpoint documentation
- Include request/response examples
- Document all parameters and their types
- Add error response examples

## 🐛 Issue Guidelines

### Bug Reports
When reporting bugs, please include:
- **Clear title**: Descriptive summary of the issue
- **Environment**: OS, Node.js version, browser (if applicable)
- **Steps to reproduce**: Detailed steps to recreate the issue
- **Expected behavior**: What you expected to happen
- **Actual behavior**: What actually happened
- **Screenshots**: If applicable
- **Additional context**: Any other relevant information

### Feature Requests
For feature requests, include:
- **Clear title**: Descriptive summary of the feature
- **Problem statement**: What problem does this solve?
- **Proposed solution**: How should this feature work?
- **Alternatives considered**: Other solutions you've thought of
- **Additional context**: Any other relevant information

## 🔀 Pull Request Guidelines

### Before Submitting
- [ ] Tests pass locally
- [ ] Code follows style guidelines
- [ ] Documentation is updated
- [ ] Commit messages follow conventional format
- [ ] Branch is up to date with main

### PR Description Template
```markdown
## Description
Brief description of changes

## Type of Change
- [ ] Bug fix
- [ ] New feature
- [ ] Breaking change
- [ ] Documentation update

## Testing
- [ ] Unit tests added/updated
- [ ] Integration tests added/updated
- [ ] Manual testing performed

## Screenshots (if applicable)

## Additional Notes
```

### Review Process
1. **Automated checks**: All CI checks must pass
2. **Code review**: At least one maintainer must review
3. **Testing**: Reviewer will test the changes
4. **Approval**: Changes must be approved before merging

## 🏷️ Versioning

We use [Semantic Versioning](https://semver.org/):
- **MAJOR**: Breaking changes
- **MINOR**: New features (backwards compatible)
- **PATCH**: Bug fixes (backwards compatible)

## 📞 Getting Help

- **Discord**: Join our community server
- **Discussions**: Use GitHub Discussions for questions
- **Issues**: Create an issue for bugs or feature requests
- **Email**: Contact maintainers directly for sensitive issues

## 🎉 Recognition

Contributors are recognized in:
- README contributors section
- Release notes for significant contributions
- Annual contributor appreciation posts

## 📝 License

By contributing to KadoWebTube, you agree that your contributions will be licensed under the MIT License.

---

Thank you for contributing to KadoWebTube! Your efforts help make YouTube automation more accessible and reliable for everyone. 🚀