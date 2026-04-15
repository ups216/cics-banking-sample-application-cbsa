# Context Update Instruction

## Purpose
This instruction guides the AI model to update existing context for the current workspace when changes occur.

## Language Detection

Before updating any context files, you must detect and use the current environment's response language:

1. **Detect Response Language**: Analyze the environment settings to determine the primary language:
   - Check system/user language settings or environment configuration
   - Identify the primary language used in project documentation and comments
   - Determine the language preference based on workspace context

2. **Apply Language Consistency**: Ensure all updated context files use the detected language:
   - Use the same language for all markdown files, comments, and documentation
   - Maintain language consistency across all updated context files
   - Follow the detected language's writing conventions and formatting

3. **Supported Languages**:
   - English (en)
   - Chinese (zh)
   - Other languages as needed based on environment detection

**IMPORTANT**: The language detection is the FIRST step before any context update. All output must consistently use the detected language throughout the entire process.

## When to Update Context
Update context when:
- New files or directories are added/removed
- Technology stack changes (new frameworks, libraries, tools)
- Data models are modified
- API endpoints are added/changed/removed
- Deployment configuration changes
- Architecture evolves
- Coding standards are updated

## Steps to Update Context

### 1. Check Existing Context
Review existing context files in `.asdm/contexts/` directory to understand current state.

### 2. Analyze Changes
Analyze what has changed in the workspace since the last context generation:
- Compare current workspace structure with documented structure
- Identify new/modified files and directories
- Detect changes in dependencies and configurations
- Review updated code patterns and conventions

### 2.5 Use Spec as Reference
Use the specs from `spec/` directory as reference points when updating context:
**Important**: Translate and adapt all spec content to the detected language, ensuring natural and accurate localization of all text, examples, and explanations.
- Compare current workspace state with spec requirements
- Customize spec content based on actual workspace analysis
- Ensure updates align with spec standards while reflecting reality

### 3. Update Specific Context Files (On-Demand)
Update context files one at a time based on user requests to ensure high-quality output:
**Each file should be updated individually and must use the detected language:**

- User specifies which context file needs updating
- Update the requested file individually using the detected language
- Maintain consistency with other context files
- Wait for user review before proceeding to the next update

Update only the context files that are affected by the changes:

#### For structural changes:
- Update `index.md` with new file tree and comments (use detected language)
- Update `standard-project-structure.md` if project organization changed (use detected language)

#### For technology changes:
- Update `index.md` technology stack section (use detected language)
- Update `standard-coding-style.md` if coding standards changed (use detected language)

#### For data model changes:
- Update `data-models.md` with new/modified models (use detected language)
- Update diagrams and relationships

#### For API changes:
- Update `api.md` with new/modified endpoints (use detected language)
- Update sample data and documentation (use detected language)

#### For deployment changes:
- Update `deployment.md` with new configuration (use detected language)
- Update deployment diagrams

#### For architecture changes:
- Update `architecture.md` with new architectural decisions (use detected language)
- Update architecture diagrams

### 4. Maintain Consistency
Ensure all context files remain consistent with each other:
- Cross-references between files should be accurate
- Terminology should be consistent across all files (using detected language)
- Diagrams should reflect current state
- Language usage should remain uniform across all updated files

### 5. Version Context
Consider adding version information or change logs to context files to track updates. Use the detected language for all version information.

## Usage
To use this instruction:
1. First detect and apply the environment's response language
2. Analyze what has changed in the workspace
3. Update the requested context file individually on-demand
4. Focus on incremental updates rather than regenerating everything from scratch
5. Always use the detected language throughout the entire update process

This phased approach ensures:
- Efficient token usage
- Higher quality output for each update
- User control over the update sequence
- Ability to adjust based on feedback
- Consistent language usage across all context files