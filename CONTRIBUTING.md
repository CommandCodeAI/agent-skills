# Contributing

We welcome contributions to awesome-skills from any framework or AI provider. Here's how you can contribute:

- Add a new skill implementation
- Improve existing skills with bug fixes or enhancements
- Share your skill implementations and use cases
- Update documentation and examples

---

## Contributing to awesome-skills

1. Fork this repository
2. Clone the repository to your local machine
3. Create a new branch for your changes
    ```bash
    git checkout -b your-github-username/new-branch-name
    ```
4. Follow the [skill creation guide](#creating-new-skills) to create a new skill
5. [Create a pull request](#pull-request-guidelines)

## Creating New Skills

### Skill Structure

Each skill must follow this structure:

```
skill-name/
├── SKILL.md          # Required: Skill instructions and metadata
├── scripts/          # Optional: Helper scripts
├── templates/        # Optional: Document templates
├── references/       # Optional: Reference files
└── LICENSE.txt       # Optional: License file (if different from repo license)
```

### Skill Requirements

1. **SKILL.md** - Must contain:
   - YAML frontmatter with `name` and `description`
   - Clear instructions for AI assistants
   - Use cases and examples
   - Prerequisites and dependencies (if any)

2. **Naming Convention**:
   - Use kebab-case for skill folder names (e.g., `file-organizer`, `changelog-generator`)
   - Keep names descriptive and concise

3. **Documentation**:
   - Include clear "When to Use This Skill" section
   - Provide real-world examples
   - Document any required dependencies or setup

### Skill Best Practices

- **Focus on specific, repeatable tasks** - Skills should solve concrete problems
- **Include clear examples** - Show both basic and advanced use cases
- **Write for AI assistants** - Instructions should be clear for AI to follow
- **Test across platforms** - Ensure skills work with Command Code and other AI assistants
- **Document prerequisites** - List any required tools, APIs, or dependencies
- **Include error handling** - Guide AI on how to handle edge cases and errors
- **Follow coding standards** - Maintain code quality and best practices

### Example Skill Template

See the [template-skill](skills/template-skill/) directory for a basic template.

## Pull Request Guidelines

### PR Title Format

Pull Request titles should follow the [Emoji-Log](https://github.com/ahmadawais/Emoji-Log) format:

- 📦 **NEW**: Skill Name - Add a new skill
- 👌 **IMPROVE**: Skill Name - An improvement to an existing skill
- 🐛 **FIX**: Skill Name - A bug fix for an existing skill
- 📖 **DOC**: Skill Name - Documentation changes for an existing skill

### PR Description

Your pull request should include:

1. **Clear description** of what the skill does and why it's useful
2. **Use cases** - When and how to use this skill
3. **Testing** - How you tested the skill (which platforms, examples)
4. **Breaking changes** - If any, clearly document them
5. **Related issues** - Link to any related issues or discussions

## Code of Conduct

Please read our [Code of Conduct](code-of-conduct.md) before contributing. We are committed to providing a welcoming and inclusive environment for all contributors.

## Questions

If you have questions about contributing:

- Check existing skills for examples
- Open an issue for discussion
- Join our [Discord](https://langbase.com/discord) community

Thank you for contributing to awesome-skills!
