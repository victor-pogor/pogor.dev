---
author: Victor Pogor
pubDatetime: 2025-01-08T21:09:18.000+10:00
title: VS Code Extension Development
slug: "1-vs-code-extension-development-pdf-syntax-highlight"
featured: true
draft: false
tags:
  - Visual Studio Code
description: "dd"
---

Intro
Why PDF as a base?
Why not using New Language Support?

## Table of contents

## Prerequisites

https://code.visualstudio.com/api/get-started/your-first-extension

First, we need the essential tools:

- [Visual Studio Code](https://code.visualstudio.com/)
- [Node.js](https://nodejs.org/)
- [Git](https://git-scm.com/)

## Initialize the extension project

```sh
npx --package yo --package generator-code -- yo code
```

```sh
# ? What type of extension do you want to create? New Extension (TypeScript)
# ? What's the name of your extension? PdfSyntaxHighlight
# ? What's the identifier of your extension? pdf-syntax-highlight
# ? What's the description of your extension? A sample VS Code extension that demonstrates how to configure PDF syntax support.
# ? Initialize a git repository? Yes
# ? Which bundler to use? webpack
# ? Which package manager to use? npm
# ? Do you want to open the new folder with Visual Studio Code? Open with `code`
```
