---
title: "Exercise - Create an Azure Function by using Visual Studio Code"
type: source
tags: [azure-functions, visual-studio-code, exercise, csharp, az204]
sources: [learn.microsoft.com_en-us_training_modules_develop-azure-functions_5-create-function-visual-studio-code.pdf]
created: 2026-06-16
updated: 2026-06-16
---

# Exercise - Create an Azure Function by using Visual Studio Code

> [!source] learn.microsoft.com_en-us_training_modules_develop-azure-functions_5-create-function-visual-studio-code.pdf

## Overview

A guided exercise (~15 minutes) for creating a C# HTTP-triggered function, testing it locally in Visual Studio Code, and deploying it to Azure.

## Tasks

1. Create a local Functions project.
2. Run the function locally.
3. Deploy and execute the function in Azure.
4. Clean up resources.

## Prerequisites

- Azure subscription.
- Visual Studio Code on a supported platform.
- .NET 8 (target framework).
- C# Dev Kit for Visual Studio Code.
- Azure Functions extension for Visual Studio Code.
- Azure Functions Core Tools v4.x.

### Install Azure Functions Core Tools (Windows)

```bash
winget uninstall Microsoft.Azure.FunctionsCoreTools
winget install Microsoft.Azure.FunctionsCoreTools
```

## Key Claims

- The exercise uses the **C# isolated worker model** with an HTTP trigger.
- Local testing uses the full Functions runtime via Azure Functions Core Tools.
- After local testing, the project is published directly to Azure from Visual Studio Code.

## Related Pages

- [[azure-functions]] – entity
- [[function-app]] – entity
- [[triggers-and-bindings]] – concept
- [[connect-functions-to-azure-services]] – previous source
- [[explore-azure-functions-development]] – development overview
