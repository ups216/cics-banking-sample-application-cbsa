# ASDM Toolset - Context Builder

toolset-id: context-builder
toolset-name: Context Builder
version: 0.0.2
updated-date: 2026-1-19
toolset-description: A toolset for building context for a workspace.


## Overview

Context Builder (toolset-id `context-builder`) is a toolset for building context for a workspace. Context is essential for any AI model to work with, it provides the model with the necessary information to generate the desired output. 

Context Builder will assist the user to build such context for a workspace automatically by using pre-defined templates and prompts, this will reduce the complexity of building context for a workspace and make it easier to use AI models.

User can install this `toolset` into a workspace and run `INSTALL.md` document using `AI Guided Installation` to initialize the toolset for the workspace. Just simply copy and paste the following prompt into your `AI Coding` tool's chat window and hit enter:

```shell
Follow instructions in .asdm/toolsets/context-builder/INSTALL.md
```

## Features

Main features of Context Builder:

- Provide user friendly shortcuts `actions` using provider's entry point to ease the process of building context for a workspace
- Provide standard `spec` for building context for a workspace, and allow user admin (Project Manager, Product Manager, Product Owner) to define their own process by customize the templates
- Act as a provider for other toolsets to use the context for working with **AI Models**, this is what is called `context injection` process, refer to [ASDM Documentation for Contenxt Injection](https://asdm.ai/docs/concepts/context-injection) for more details.

## Toolset Installation Process

`INSTALL.md` will setup the toolset with the following steps:

- Create `.asdm/contexts` directory for Context Builder's workspace
- Detect the current `Agentic Engine` provider, e.g. Claude Code, GitHub Copilot, Tencent CodeBuddy etc. （Use hard-coded provider name for now, e.g. CodeBuddy ）
- Create shortcuts commands for `Context Builder` in provider's entry point, e.g. `.claude/commands`, `.github/prompts`, `.codebuddy/commands` etc.

## Toolset Workflow

Once `Context Builder` is installed, user can use the following commands to build or update context for the current workspace

- `/asdm-context-build`: build context for the current workspace
- `/asdm-context-update`: update context for the current workspace

The `INSTALL.md` should also include instructions for initializing the toolset for the current workspace, e.g. running `/asdm.content.build` to build context for the current workspace. This is as simple as the following prompt:

```shell
Follow the instructions in .asdm/toolsets/context-builder/actions/asdm-context-build.md
```

## Toolset Structure

The structure of the toolset is as follows:

```
.asdm/toolsets/context-builder/
├── INSTALL.md                                  ## Installation instructions for the toolset, contains prompts for AI Guided Installation
├── README.md                                   ## Current docuent
├── actions                                     ## Instructions for Context Builder
│   ├── asdm-context-build.md                        ## Instruction for building/initializing context for a workspace
│   └── asdm-context-update.md                       ## Instruction for updating context for a workspace
├──spec                                         ## Templates for Context Builder
│   ├── index.md                           ## Template for building Index for current workspace's context content
│   ├── standard-project-structure.md      ## Template for building Standard Project Structure for current workspace
│   ├── standard-coding-style.md           ## Template for building Standard Coding Style for current workspace
│   ├── data-models.md                     ## Template for building Data Models related context for current workspace
│   ├── deployment.md                      ## Template for building Deployment related context for current workspace
│   └── api.md                             ## Template for building API related context for current workspace
│   └── architecture.md                    ## Template for building Architecture related context for current workspace
```

Additional Explaination of the structure:

- `index.md`: act as a index/guide for **AI Model** to follow in order to find the related context according to the current job, including: 
    - a `tree-view` of the current workspace's file system and make sure each node of tree has necessary comments to guide the **AI Model** to find the related context. 
    - necessary technical details of the current workspace, e.g. technology stack, frameworks, libraries, tools etc.
    - necessary business details of the current workspace, e.g. business domain, business process, business rules etc.
    - necessary instructions for compiling, buiding, debugging and testing the current workspace, this is for **AI Model** to know how to work with the current workspace.
    - files links for other context files in `.asdm/contexts/` directory
- `standard-project-structure.md`: this is the proposed standard project structure for a software project, it should be related to specific technology stack, e.g. Java, Python, Go, TypeScript, C# etc and also related to the frameworks used, e.g. Spring Boot, Flask, Django, Express, FastAPI etc.
- `context.standard-coding-style.md`: this is the proposed standard coding style for a software project, it should be related to specific technology stack, e.g. Java, Python, Go, TypeScript, C# etc and also related to the frameworks used, e.g. Spring Boot, Flask, Django, Express, FastAPI etc.
- `data-models.md`: this is the current data models for the current workspace, it should include necessary information for **AI Models** to understand, design, modify and implement the data models, including:
    - data models' definitions, e.g. table schema, class definitions, object definitions, data structures etc.
    - data models' relationships, e.g. table relationships, class relationships, object relationships, data structures relationships etc.
    - data models' constraints, e.g. table constraints, class constraints, object constraints, data structures constraints etc.
    - data model & flow diagrams using mermaid, e.g.
        - entity relationship diagram, 
        - class diagram, 
        - object diagram, 
        - data structure diagram
        - sequence diagram
        - state diagram etc.
- `deployment.md`: this is the current deployment related context for the current workspace, it should include necessary information for **AI Models** to understand, design, modify and implement the deployment process, including:
    - deployment process, e.g. deployment pipeline, deployment process, deployment strategy etc.
    - deployment environment, e.g. development environment, staging environment, production environment etc.
    - deployment configuration, e.g. deployment configuration, deployment variables etc.
    - use `mermaid` to draw deployment diagrams, e.g. deployment diagram, deployment process diagram, deployment environment diagram etc.
- `api.md`: this is the current API related context for the current workspace, it should include necessary information for **AI Models** to understand, design, modify and implement the API, including:
    - API meta data, including endpoint url
    - API definitions in a table format, e.g. API endpoints, API methods, API parameters, API responses, API status codes, API security and a description for each API.
    - API testing, e.g. API testing, API testing tools, API testing strategies etc.
    - make sure `sample data` is included in the API testing section, e.g. sample data for API parameters, sample data for API responses etc.
    - make sure necessary links to the source code file is included so that **AI Models** can find the source code file to understand more details when required.
- `architecture.md`: this is the current architecture related context for the current workspace, it should include necessary information for **AI Models** to understand, design, modify and implement the architecture, including:
    - architecture diagrams using mermaid, e.g. component diagram, container diagram, deployment diagram etc.
    - architecture components, e.g. services, databases, message brokers, load balancers etc.
    - architecture relationships, e.g. service relationships, database relationships, message broker relationships etc.

## Toolset Workspace

Here is an example of the toolset workspace to be initialized by `asdm-context-build.md`, the worksapce should be created under `.asdm/contexts/` directory and used by `context-builder` toolset to build context for the current workspace, also allow other toolsets to use the context for working with **AI Models**, which is called `context injection` process.

```
.asdm/contexts/
├── index.md                               ## Index for current workspace's context content
├── standard-project-structure.md          ## Standard Project Structure for current workspace
├── standard-coding-style.md               ## Standard Coding Style for current workspace
├── data-models.md                         ## Data Models related context for current workspace
├── deployment.md                          ## Deployment related context for current workspace
├── api.md                                 ## API related context for current workspace
├── architecture.md                        ## Architecture related context for current workspace
```


## Copyright & License

Copyright (c) 2026 LeansoftX.com & iSoftStone. All rights reserved.

Licensed under the PROPRIETARY SOFTWARE LICENSE. See [LICENSE](LICENSE) in the project root for license information.
