# Instructions for asdm-context-build action

## Purpose
This instruction guides the AI model to generate context for the current workspace using Context Builder toolset.

## Language Detection

Before generating context files, you must detect and use the current environment's response language:

1. **Detect Response Language**: Analyze the environment settings to determine the primary language:
   - Check system/user language settings or environment configuration
   - Identify the primary language used in project documentation and comments
   - Determine the language preference based on workspace context

2. **Apply Language Consistency**: Ensure all generated context files use the detected language:
   - Use the same language for all markdown files, comments, and documentation
   - Maintain language consistency across all generated context files
   - Follow the detected language's writing conventions and formatting

3. **Supported Languages**:
   - English (en)
   - Chinese (zh)
   - Other languages as needed based on environment detection

**IMPORTANT**: The language detection is the FIRST step before any context generation. All output must consistently use the detected language throughout the entire process.

## Steps to Generate Context

### 1. Initialize Context Directory
Create the `.asdm/contexts/` directory in the workspace root if it doesn't exist.

### 2. Generate Initial Context File (index.md)
Generate **only the index.md** file first in the `.asdm/contexts/` directory.
**Ensure the generated file uses the detected language from the Language Detection step:**

1. **index.md** - Workspace index and guide
   - Provide an overview of the entire workspace
   - Include navigation links to other context files (to be generated later)
   - Summarize the workspace structure and key components

**Important**: This step generates ONLY index.md to avoid excessive token usage and maintain high generation quality.

### 3. Generate Additional Context Files (On-Demand)
After reviewing index.md, the user can request generation of additional context files one at a time:
**Each subsequent file should be generated individually and must use the same detected language:**

2. **standard-project-structure.md** - Standard project structure
3. **standard-coding-style.md** - Standard coding style
4. **data-models.md** - Data models and relationships
5. **deployment.md** - Deployment configuration
6. **api.md** - API definitions and documentation
7. **architecture.md** - Architecture overview

**Process for each additional file**:
- User specifies which file to generate next
- Generate the requested file individually using the detected language
- Maintain consistency with index.md and previously generated files
- Wait for user review before proceeding to the next file

This phased approach ensures:
- Efficient token usage
- Higher quality output for each file
- User control over the generation sequence
- Ability to adjust based on feedback

### 4. Analyze Current Workspace
Before generating context, analyze the current workspace to understand:
- Technology stack and frameworks
- Project structure and organization
- Existing code patterns and conventions
- Data models and database schemas
- API endpoints and documentation
- Deployment configuration and environment

### 5. Use Spec
Use the specs from `spec/` directory as starting points, but customize them based on the actual workspace analysis.
**Important**: Translate and adapt all spec content to the detected language, ensuring natural and accurate localization of all text, examples, and explanations.

### 6. Include Mermaid Diagrams
Where applicable, include mermaid diagrams for:
- Entity relationship diagrams
- Class diagrams
- Sequence diagrams
- Deployment diagrams
- Architecture diagrams

### 7. Provide Sample Data
For API definitions, include sample request/response data.

### 8. Link to Source Code
Include links to relevant source code files for detailed reference.

## Usage
To use this instruction, simply follow the steps above. The AI model should analyze the workspace and generate comprehensive context files that can be used by other toolsets through context injection.