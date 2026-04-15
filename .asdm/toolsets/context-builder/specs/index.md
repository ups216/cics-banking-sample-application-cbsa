# Workspace Context Index

## Overview
This document serves as the index and guide for AI models to understand and work with this workspace. It provides a structured overview of the workspace content and guides AI models to find relevant context.

## Workspace Information

### Basic Information
- **Workspace Name**: [Workspace Name]
- **Description**: [Brief description of the workspace purpose]
- **Created Date**: [Creation date]
- **Last Updated**: [Last update date]

### Technology Stack
- **Primary Language**: [e.g., TypeScript, Python, Java]
- **Frameworks**: [e.g., React, Spring Boot, Express]
- **Build Tools**: [e.g., npm, yarn, Maven, Gradle]
- **Database**: [e.g., PostgreSQL, MongoDB, MySQL]
- **Testing Framework**: [e.g., Jest, pytest, JUnit]
- **Deployment Platform**: [e.g., Docker, Kubernetes, Cloud Platform]

### Business Context
- **Business Domain**: [e.g., E-commerce, Healthcare, Finance]
- **Key Business Processes**: [List main business processes]
- **Business Rules**: [Important business rules and constraints]

## Workspace Structure

### File Tree with Guidance
```
[Workspace Root]/
├── .asdm/                          # ASDM configuration and toolsets
│   ├── contexts/                   # Context files (this directory)
│   └── toolsets/                   # Installed toolsets
├── src/                            # Source code directory
│   ├── main/                       # Main application code
│   │   ├── [language-specific structure]
│   │   └── ...
│   └── test/                       # Test code
│       └── ...
├── config/                         # Configuration files
│   ├── [environment configs]
│   └── ...
├── docs/                           # Documentation
│   ├── api/                        # API documentation
│   └── ...
├── scripts/                        # Build and utility scripts
└── [other directories]             # Additional project directories
```

### Key Directories Explanation
- **`.asdm/contexts/`**: Contains all context files for AI model reference
- **`src/main/`**: Primary source code - AI should focus here for implementation
- **`src/test/`**: Test files - AI should maintain test coverage
- **`config/`**: Configuration files - AI should understand environment-specific settings
- **`docs/`**: Documentation - AI should reference for API and usage details

## Development Guidelines

### Building and Compilation
```bash
# Build command
[Command to build the project]

# Development server
[Command to start development server]

# Production build
[Command to create production build]
```

### Testing
```bash
# Run tests
[Command to run all tests]

# Run specific test
[Command to run specific test suite]

# Test coverage
[Command to generate test coverage report]
```

### Code Quality
- **Linting**: [Linting command and configuration]
- **Formatting**: [Code formatting command]
- **Static Analysis**: [Static analysis tools and commands]

## Context Files Reference

This workspace has the following context files available in `.asdm/contexts/`:

1. **[asdm.standard-project-structure.md](./asdm.standard-project-structure.md)** - Standard project structure and organization
2. **[asdm.standard-coding-style.md](./asdm.standard-coding-style.md)** - Coding standards and style guidelines
3. **[asdm.data-models.md](./asdm.data-models.md)** - Data models, relationships, and diagrams
4. **[asdm.deployment.md](./asdm.deployment.md)** - Deployment configuration and processes
5. **[asdm.api.md](./asdm.api.md)** - API definitions, endpoints, and documentation
6. **[asdm.architecture.md](./asdm.architecture.md)** - System architecture and design decisions

## AI Model Guidance

### How to Use This Context
1. **Start with this index** to understand the workspace structure
2. **Refer to specific context files** based on the task at hand
3. **Follow the development guidelines** for building, testing, and deployment
4. **Maintain consistency** with existing patterns and conventions

### Common Tasks
- **Adding new features**: Check architecture and data models first
- **Modifying APIs**: Refer to API documentation and update accordingly
- **Database changes**: Update data models and migration scripts
- **Deployment updates**: Follow deployment process documentation

### Troubleshooting
- If something doesn't work as expected, check the relevant context file
- For build issues, verify dependencies and configuration
- For runtime issues, check deployment and environment configuration

## Version History
| Version | Date | Changes | Author |
|---------|------|---------|--------|
| 1.0.0 | [Date] | Initial context creation | [Author] |
| [Next] | [Date] | [Description of changes] | [Author] |

---

*This context file is maintained by the Context Builder toolset. Use `/context-update-instruction` to update when workspace changes occur.*