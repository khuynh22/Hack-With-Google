# Contributing to Device Performance Monitoring

Thank you for your interest in contributing to our Device Performance Monitoring project! 🎉

## Table of Contents

- [Getting Started](#getting-started)
- [How to Contribute](#how-to-contribute)
- [Reporting Bugs](#reporting-bugs)
- [Suggesting Enhancements](#suggesting-enhancements)
- [Code of Conduct](#code-of-conduct)
- [Contact](#contact)

## Getting Started

Before you begin contributing, please:

1. **Read the README** - Familiarize yourself with the project's goals and current features
2. **Check existing issues** - See if someone else has already reported the same idea or bug
3. **Understand the tech stack** - This project is built with AppSheet and Google Workspace

## How to Contribute

### For Non-Technical Contributors

You can contribute by:

- 📝 **Documentation** - Help improve our documentation, fix typos, add examples
- 💡 **Feature Ideas** - Share ideas for new features or improvements
- 🎨 **Design Feedback** - Provide UI/UX feedback on the app interface
- 📊 **Use Case Studies** - Share how you might use this in your industry
- 🌐 **Translations** - Help translate documentation to other languages

### For Technical Contributors

Since this is an AppSheet-based project, traditional code contributions work differently:

1. **App Logic & Configuration**
   - AppSheet app definitions are not stored in this repository
   - To contribute app improvements, you'll need to:
     - Copy the app to your AppSheet account
     - Make and test your changes
     - Document your changes with screenshots
     - Share your improvements via issue or email

2. **Data Structure Improvements**
   - Suggest improvements to the data schema
   - Provide sample data or test cases
   - Document edge cases and scenarios

3. **Integration Scripts**
   - Google Apps Script for GitHub integration
   - Automation workflows (n8n, Zapier, etc.)
   - API integration examples

4. **Documentation**
   - Improve setup guides
   - Add troubleshooting sections
   - Create video tutorials or guides

## Reporting Bugs

Found a bug? Help us fix it!

### Before Submitting a Bug Report

- Check if the bug has already been reported in [Issues](../../issues)
- Try to reproduce the bug in a fresh environment
- Collect relevant information (screenshots, error messages, etc.)

### How to Submit a Good Bug Report

Create an issue with the following information:

**Title:** Clear, descriptive title

**Description:**
- **What happened:** Describe the bug
- **Expected behavior:** What you expected to happen
- **Steps to reproduce:** Step-by-step guide to reproduce the issue
- **Screenshots:** If applicable
- **Environment:**
  - AppSheet version/tier
  - Device type (mobile/desktop)
  - Browser (if applicable)
  - Operating system

**Example:**

```
Title: OCR fails to read voltage values from analog meters

Description:
When using the OCR feature on analog meters (non-digital displays), 
the system fails to extract voltage values correctly.

Expected: OCR should read analog meter displays
Actual: Returns "Unable to read value" error

Steps to Reproduce:
1. Open Audit Log
2. Take photo of analog meter
3. Attempt OCR scan
4. Error appears

Environment:
- AppSheet Free tier
- iPhone 12, iOS 16
- Safari browser
```

## Suggesting Enhancements

We welcome feature suggestions!

### Before Suggesting an Enhancement

- Check if it's already suggested in [Issues](../../issues)
- Consider if it aligns with the project's goals
- Think about how it benefits the target users (electricians, utility companies)

### How to Submit a Good Enhancement Suggestion

Create an issue with:

**Title:** Feature: [Your feature name]

**Description:**
- **Problem:** What problem does this solve?
- **Solution:** Your proposed solution
- **Alternatives:** Other solutions you considered
- **Benefits:** Who benefits and how?
- **Implementation ideas:** If you have technical insights

**Example:**

```
Title: Feature: Weather-based predictive maintenance

Problem:
Extreme weather often causes device failures, but there's no 
proactive warning system.

Solution:
Integrate weather API to send preemptive alerts when severe 
weather is forecast near device locations.

Benefits:
- Reduces emergency callouts
- Allows proactive deployment of technicians
- Minimizes downtime

Implementation:
- Connect to weather API (OpenWeather, Weather.com)
- Create AppSheet bot to check forecasts daily
- Send alerts when severe weather detected
```

## Code of Conduct

### Our Standards

- **Be Respectful:** Treat everyone with respect and kindness
- **Be Collaborative:** Work together, share knowledge
- **Be Professional:** Keep discussions focused and constructive
- **Be Inclusive:** Welcome contributors of all backgrounds and skill levels

### Unacceptable Behavior

- Harassment or discriminatory language
- Personal attacks or trolling
- Publishing others' private information
- Any conduct that would be inappropriate in a professional setting

## Development Workflow

Since AppSheet apps cannot be version-controlled traditionally:

1. **Fork the repository** (for documentation changes)
2. **Create a branch** for your changes
3. **Make your changes**
   - Update documentation
   - Add new guides or examples
   - Improve existing content
4. **Test your changes** (ensure links work, formatting is correct)
5. **Submit a Pull Request** with a clear description

### Pull Request Guidelines

- Clear, descriptive title
- Detailed description of changes
- Reference any related issues
- Include screenshots for visual changes
- Ensure all links work
- Follow existing documentation style

## Getting Help

Need help contributing?

- 📧 **Email:** timhuynhwork@gmail.com
- 💬 **Discussions:** Use GitHub Discussions for questions
- 🐛 **Issues:** Check existing issues for similar questions

## Recognition

All contributors will be acknowledged in our documentation!

### Types of Contributions We Recognize

- 📝 Documentation improvements
- 🐛 Bug reports and fixes
- 💡 Feature suggestions
- 🎨 UI/UX feedback
- 🧪 Testing and quality assurance
- 📚 Educational content (tutorials, videos)

## License

By contributing, you agree that your contributions will be subject to the same proprietary license as the project. All contributors retain their copyright, but grant the project owner rights to use the contributions.

---

## Questions?

Don't hesitate to reach out if you have any questions about contributing. We appreciate all forms of contribution, no matter how small!

**Contact:** timhuynhwork@gmail.com

Thank you for helping make Device Performance Monitoring better! 🙏
