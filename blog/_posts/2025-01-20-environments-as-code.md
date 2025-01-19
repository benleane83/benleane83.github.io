---
layout: post
title: From Infrastructure-as-Code to Environment-as-Code: A Quick Intro
description: >
  A look at Microsoft's current Environment-as-Code offerings and why they're becoming an essential part of a developer's toolkit.
image: /assets/img/blog/environment-as-code-intro.png
sitemap: true
---

## From Infrastructure-as-Code to Environment-as-Code: A Quick Intro

Environment-as-Code is an 'under the radar' trend that you might have missed underneath all the AI hype of late.

It builds on Infrastructure-as-Code concepts, but with focus on configuring the applications and services that run on top of that infrastructure.
This is powerful for Dev/Test environments (which can need additional tooling or setup beyond Prod), or for any environment that needs re-deploying on a frequent basis.
    
Microsoft and GitHub have been evolving this concept for a while now, with key product releases including:
- **Devcontainers** for VSCode in 2020
- **GitHub Codespaces** in 2021
- **Microsoft Dev Box** in 2023
- **Dev Home** and **Winget Configuration** in 2023 (Dev Home remains in public preview)
    
We've also seen **Azure Deployment Environments** and **Azure Developer CLI** released in 2023, which are hybrid IaC/EaC tools, but aimed largely at developers.

What these tools share is that they support definition of a full dev environment in code files - including a base image, runtimes/SDKs, development tools like IDEs (including extensions), and cloned repos or projects. Running that code allows you to get from zero to running/debugging your apps in minutes rather than hours or days!

That makes them perfect for a range of scenarios including:
- Development teams who onboard new developers often
- Apps with complex deployments or pre-reqs that suffer from 'works on my machine' issues
- Open-source or public projects that want to minimise effort for others to contribute
- Cloud Native development scenarios where app components are re-deployed frequently
    
### So which tool is right for me?
There's a lot of choices there, and it's easy to get confused on which one you should pick up. Here's how I think of them currently:
- **Dev Box** suits when you need a full Windows VM image with UI control and desktop app support
- **Devcontainers** allow for local Docker container-based development with Linux containers. Supports VS Code plus some support for other IDEs such as IntelliJ
- **GitHub Codespaces** provides a managed cloud-hosted experience that uses the Devcontainer spec for configuration (VS Code only)
- **Azure Deployment Environments** and **Azure Developer CLI (AZD)** are for managing your app environments themselves in Azure

What amazes me about these EaC tools is that many Microsoft and 3rd party templates and sample apps have adopted them in their repos, meaning you may already have them and didn't realise!

### How do I know what to look for?
- Devcontainer definitions will appear within the **.devcontainer/** folder, containing one or more devcontainer.json files. *Hint: The presence of these will normally trigger a popup in VS Code asking if you want to reopen your project in a container*
- WinGet Configuration files (used by Dev Box & Dev Home) often appear within the **.configurations/** folder, as .yaml files
- Azure Developer CLI configurations will appear as an **azure.yaml** file in your project root, along with an **.azure/** folder holding your environment definitions, and an **infra/** folder with the IaC scripts themselves
- With **Dev Box** and **Azure Deployment Environments** you can also reference configs from a Dev Center Catalog (a linked repo holding your yaml/json configurations)
    
### Show me an example:
A great intro to EaC concepts is the ToDo reference app, which comes in a few flavours such as this C# one:
[Azure-Samples/todo-csharp-sql](https://github.com/Azure-Samples/todo-csharp-sql/)

It features:
- A devcontainer config for local debugging or Codespaces. It uses a .NET 8 container image, with .NET runtimes, nodeJS, AZD, and VS Code + a bunch of extensions added
- An AZD azure.yaml config which deploys the project to Azure: a VITE NodeJS App Service for the web frontend, and a C# App Service for the API app. It also features a SQL DB, Key Vault, and APIM instance all configured to work together
- CI/CD pipelines for both Azure DevOps (in the .azdo folder) and GitHub Actions (in the .github/workflows folder), which run an azd based deploy

See the project README for instructions on getting started locally or in Azure.
    
### Too easy and want something more involved?
Try [Azure-Samples/azure-search-openai-demo](https://github.com/Azure-Samples/azure-search-openai-demo) - a popular RAG accelerator app using Azure OpenAI, AI Search, Container Apps, Cosmos DB and many more Azure services. You'll find all the same config templates, allowing you to run this locally, in Codespaces, or fully in Azure.

Be aware this one does take longer to deploy, but it's a great example of how far you can take the EaC concept.

If you're looking for Winget Configurations, there's also [Azure-Samples/eShopOnAzure](https://github.com/Azure-Samples/eShopOnAzure), a .NET Aspire application which showcases these as well as AZD deployment.
    
### Want to learn more?
- [Development containers](https://containers.dev/)
- [GitHub Codespaces](https://github.com/features/codespaces)
- [Microsoft Dev Box – Dev Workstation in the Cloud | Microsoft Azure](https://azure.microsoft.com/en-us/products/dev-box)
- [WinGet Configuration | Microsoft Learn](https://learn.microsoft.com/en-us/windows/package-manager/configuration/)
