# Context Builder Toolset Installation

**Toolset ID:** `context-builder`

## Overview
This document provides instructions for installing and setting up the Context Builder toolset in a workspace. Context Builder helps build comprehensive context for AI models to work effectively with your codebase.

## AI Guided Installation
To install this toolset using AI Guided Installation, copy and paste the following prompt into your AI Coding tool's chat window:

```shell
Follow instructions in .asdm/toolsets/context-builder/INSTALL.md
```

## Installation Steps

### 1. Create `.asdm/contexts` directory for Context Builder's workspace

Create the directory structure for storing context files:

```bash
mkdir -p .asdm/contexts
```

### 2. Detect the current `Agentic Engine` provider

Detect the current AI coding assistant provider (e.g., Claude Code, GitHub Copilot, Tencent CodeBuddy). Using the following guidelines to detect the provider:

- If `.claude` directory exists, use `Claude Code`
- If `.github` directory exists, use `GitHub Copilot`
- If `.codebuddy` directory exists, use `Tencent CodeBuddy`
- If no such folder is found in the current workspace, give user a prompt to select a provider manually

### 3. Create shortcuts commands for Context Builder (toolset ID: `context-builder`) in provider's entry point

Create shortcut commands in the appropriate location based on the detected provider. The installation process is consistent across all providers - we use `cat` to concatenate provider-specific frontmatter with the actual instruction content:

#### For Claude Code (`.claude/commands/`):
Claude Code uses Markdown files with Frontmatter metadata for slash commands. Create commands by concatenating Claude-specific frontmatter with instruction content:

```bash
mkdir -p .claude/commands/

# Context Generation command
cat > .claude/commands/asdm-context-build.md << 'EOF'
---
description: "Generate initial context for the workspace"
argument-hint: "[additional prompt]"
---

EOF
cat .asdm/toolsets/context-builder/actions/asdm-context-build.md >> .claude/commands/asdm-context-build.md

# Context Update command
cat > .claude/commands/asdm-context-update.md << 'EOF'
---
description: "Update existing context when workspace changes"
argument-hint: "[additional prompt]"
---

EOF
cat .asdm/toolsets/context-builder/actions/asdm-context-update.md  >> .claude/commands/asdm-context-update.md 
```

#### For GitHub Copilot (`.github/prompts/`):
GitHub Copilot uses `.prompt.md` files with YAML frontmatter. Create prompt files by concatenating GitHub-specific frontmatter with instruction content:

```bash
mkdir -p .github/prompts/

# Context Generation prompt
cat > .github/prompts/asdm-context-build.prompt.md << 'EOF'
---
agent: 'agent'
description: 'Generate initial context for the workspace'
argument-hint: 'Enter additional prompt'
---

EOF
cat .asdm/toolsets/context-builder/actions/asdm-context-build.md >> .github/prompts/asdm-context-build.prompt.md

# Context Update prompt
cat > .github/prompts/asdm-context-update.prompt.md << 'EOF'
---
agent: 'agent'
description: 'Update existing context when workspace changes'
argument-hint: 'Enter additional prompt'
---

EOF
cat .asdm/toolsets/context-builder/actions/asdm-context-update.md >> .github/prompts/asdm-context-update.prompt.md
```

#### For Tencent CodeBuddy (`.codebuddy/commands/`):
CodeBuddy doesn't support frontmatter, so simply copy the instruction files as-is:

```bash
mkdir -p .codebuddy/commands/

# Copy instruction files directly (no frontmatter needed)
cp .asdm/toolsets/context-builder/actions/casdm-context-builder.md .codebuddy/commands/
cp .asdm/toolsets/context-builder/actions/asdm-context-update.md .codebuddy/commands/
```

### 4. Manual Usage for Other Providers

If your AI coding assistant provider is not detected by the automatic detection logic (Claude Code, GitHub Copilot, or Tencent CodeBuddy), you can still use the Context Builder manually. Follow these steps:

#### Direct Instruction Usage
You can directly use the instruction files by copying their relative paths and pasting them into your AI coding assistant's chat window:

1. **Navigate to the instruction files**:
   ```bash
   cd .asdm/toolsets/context-builder/actions/
   ```

2. **Right-click on the desired instruction file** and copy its relative path:
   - For context generation: `asdm-context-build.md`
   - For context update: `casdm-context-update.md`

3. **Enter a prompt** in your AI coding assistant:
   ```
   Follow the instructions in {relative path to instruction file}
   ```

## Initializing Context Builder

### Initial Context Generation
After installation, initialize the toolset by generating initial context for your workspace:

```shell
Follow the instructions in .asdm/toolsets/context-builder/actions/asdm-context-build.md
```

This will:
1. Analyze your workspace structure and technology stack
2. Generate comprehensive context files in `.asdm/contexts/` directory
3. Create an index and guide for AI models to understand your workspace

### Available Commands
Once installed, you can use the following commands:

1. **`/asdm-context-build`** - Generate initial context for the workspace
2. **`/asdm-context-update`** - Update existing context when workspace changes

## Context Files Structure
The toolset will create the following context files in `.asdm/contexts/`:

1. **`index.md`** - Workspace index and guide for AI models
2. **`standard-project-structure.md`** - Standard project structure
3. **`standard-coding-style.md`** - Coding standards and style guidelines
4. **`data-models.md`** - Data models and relationships
5. **`deployment.md`** - Deployment configuration and processes
6. **`api.md`** - API definitions and documentation
7. **`architecture.md`** - System architecture and design decisions

## Verification

After installation, verify that:

1. The `.asdm/contexts` directory exists for Context Builder
2. Shortcut commands for Context Builder (toolset ID: `context-builder`) are created in the appropriate provider directory (if using Claude Code, GitHub Copilot, or Tencent CodeBuddy)
3. The Context Builder toolset files are located in `.asdm/toolsets/context-builder` (toolset ID: `context-builder`)

**For other providers**: Verify that you can access the instruction files at:
- `.asdm/toolsets/context-builder/actions/asdm-context-build.md`
- `.asdm/toolsets/context-builder/actions/asdm-context-update.md`

## Usage Examples

### Generating Context for a New Workspace
```shell
# First, install the toolset using AI Guided Installation
Follow instructions in .asdm/toolsets/context-builder/INSTALL.md

# Then generate initial context
Follow the instructions in .asdm/toolsets/context-builder/actions/asdm-context-build.md
```

### Updating Context After Changes
```shell
# When you make significant changes to your workspace
Follow the instructions in .asdm/toolsets/context-builder/actions/asdm-context-update
```

## Usage

### For Supported Providers (Claude Code, GitHub Copilot, Tencent CodeBuddy)
Once installed, you can use the following commands:

- `/asdm-context-build {additional prompt}`: Generate initial context for the workspace
- `/asdm-context-update {additional prompt}`: Update existing context when workspace changes

### For Other Providers (Manual Usage)
If your provider is not automatically detected, you can manually use the instructions by following the steps in the "Manual Usage for Other Providers" section above.

## Notes

- This installation process assumes you have the necessary permissions to create directories and files
- The actual implementation of the commands will be handled by the AI model using the templates and instructions provided in Context Builder (toolset ID: `context-builder`)
- Make sure to customize the provider-specific setup based on your actual AI coding assistant
- The toolset ID `context-builder` should be used consistently when referring to Context Builder in commands and documentation
- **For providers not in the detection logic**: Users can manually use the instruction files by copying their relative paths and entering prompts like "follow the instructions in .asdm/toolsets/context-builder/actions/asdm-context-build.md"

## Integration with Other Toolsets
Context Builder can be used as a provider for other toolsets through **context injection**. Other toolsets can reference the context files to understand the workspace in order to ground the generated context to the codebase.

### Getting Help
For issues with Context Builder toolset, refer to:
- [ASDM Documentation](https://asdm.ai/docs)
- Toolset README: `.asdm/toolsets/context-builder/README.md`
- Context files in `.asdm/contexts/`

## License
Copyright (c) 2022 LeansoftX.com. All rights reserved.

Licensed under the PROPRIETARY SOFTWARE LICENSE. See [LICENSE](LICENSE) in the project root for license information.

---

*This installation document is part of the Context Builder toolset. Use the context generation instruction to create workspace-specific context files.*