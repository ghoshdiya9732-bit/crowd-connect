# 🤝 Contributing to Crowd-Connect

Thank you for your interest in contributing! This document provides guidelines and instructions for contributing.

## Code of Conduct

- Be respectful and inclusive
- Provide constructive feedback
- Help others learn and grow
- Report issues responsibly

## How to Contribute

### 1. Report Bugs

**Before submitting a bug report:**
- Check if the issue already exists
- Provide a clear description
- Include steps to reproduce
- Mention your environment (OS, Node version, etc.)

**Submit a bug report:**
- Go to [GitHub Issues](https://github.com/ghoshdiya9732-bit/crowd-connect/issues)
- Click "New Issue"
- Use the bug report template
- Provide as much detail as possible

### 2. Suggest Enhancements

- Explain the use case
- Provide examples
- Describe expected behavior
- Consider potential implementation

### 3. Submit Pull Requests

#### Setup Development Environment

```bash
# 1. Fork the repository
# 2. Clone your fork
git clone https://github.com/YOUR_USERNAME/crowd-connect.git
cd crowd-connect

# 3. Create a feature branch
git checkout -b feature/your-feature-name

# 4. Install dependencies
npm install

# 5. Make your changes
# 6. Test your changes
npm run dev

# 7. Commit with meaningful messages (see Commit Guidelines)
git commit -m "feat: add new feature description"

# 8. Push to your fork
git push origin feature/your-feature-name

# 9. Create a Pull Request on GitHub
```

## Commit Guidelines

Follow the conventional commits format:

```
<type>(<scope>): <subject>

<body>

<footer>
```

### Types
- **feat**: A new feature
- **fix**: A bug fix
- **docs**: Documentation changes
- **style**: Code style changes (formatting, semicolons, etc.)
- **refactor**: Code refactoring
- **perf**: Performance improvements
- **test**: Adding or updating tests
- **chore**: Maintenance tasks

### Examples

```bash
git commit -m "feat(campaigns): add campaign filtering by category"
git commit -m "fix(auth): resolve JWT token expiration issue"
git commit -m "docs(readme): update installation instructions"
git commit -m "refactor(api): improve error handling middleware"
```

## Code Style Guidelines

### JavaScript/Node.js

```javascript
// Use const/let, avoid var
const API_URL = 'http://localhost:5000';

// Use async/await
async function fetchCampaigns() {
  try {
    const campaigns = await Campaign.find();
    return campaigns;
  } catch (error) {
    console.error(error);
  }
}

// Use meaningful variable names
const isValidEmail = email => /^[^\s@]+@[^\s@]+\.[^\s@]+$/.test(email);

// Add comments for complex logic
// Calculate total donations for a campaign
const totalDonations = donations.reduce((sum, d) => sum + d.amount, 0);
```

### File Organization

```
src/
├── models/        # Mongoose schemas
├── routes/        # API endpoints
├── middleware/    # Express middleware
├── utils/         # Helper functions
├── config/        # Configuration files
└── controllers/   # Business logic (if applicable)
```

## Testing

```bash
# Run tests (when available)
npm test

# Check code coverage
npm run coverage
```

## Documentation

- Update README.md for user-facing changes
- Add JSDoc comments to functions
- Update SETUP.md for environment changes
- Document new API endpoints

### JSDoc Example

```javascript
/**
 * Create a new campaign
 * @param {Object} campaignData - Campaign details
 * @param {string} campaignData.title - Campaign title
 * @param {string} campaignData.description - Campaign description
 * @param {number} campaignData.goal - Fundraising goal
 * @returns {Promise<Object>} Created campaign object
 * @throws {Error} If validation fails
 */
async function createCampaign(campaignData) {
  // Implementation
}
```

## Pull Request Process

1. **Before submitting:**
   - Ensure code follows style guidelines
   - Update documentation
   - Test thoroughly
   - Rebase on latest main branch

2. **PR Description should include:**
   - What changes were made
   - Why they were made
   - Related issue numbers (fixes #123)
   - Screenshots if UI changes

3. **PR Example:**

```markdown
## Description
Adds filtering functionality to campaigns page.

## Related Issues
Closes #42

## Changes Made
- Added category filter dropdown
- Implemented backend filtering logic
- Updated UI with new filter options

## Testing
- Tested filtering with multiple categories
- Verified API response
- Tested on responsive designs

## Screenshots
[Before] [After]
```

4. **Review Process:**
   - Maintainers will review within 3-5 days
   - Address feedback and comments
   - Update PR based on suggestions

5. **Merge:**
   - Squash commits if requested
   - PR gets merged by maintainer

## Development Workflow

```
main (stable)
  ├── develop (latest features)
  ├── feature/feature-name (your contribution)
  ├── fix/issue-name (bug fixes)
  └── docs/update-name (documentation)
```

## Need Help?

- Check [existing issues](https://github.com/ghoshdiya9732-bit/crowd-connect/issues)
- Read [SETUP.md](SETUP.md) for environment setup
- Review [GIT_WORKFLOW.md](GIT_WORKFLOW.md) for Git practices
- Reach out on GitHub Discussions

## Recognition

Contributors will be recognized in:
- CONTRIBUTORS.md file
- GitHub contributors page
- Release notes

---

Happy contributing! 🚀
