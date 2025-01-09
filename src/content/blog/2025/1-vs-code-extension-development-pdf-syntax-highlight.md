---
author: Victor Pogor
pubDatetime: 2025-01-08T21:09:18.000+10:00
title: VS Code Extension Development
slug: "1-vs-code-extension-development-pdf-syntax-highlight"
featured: true
draft: false
tags:
  - Visual Studio Code
  - PDF
description: "dd"
---

Intro
Why PDF as a base?
Why not using New Language Support?
ORCID integration?

## Table of contents

## PDF types

[ISO 32000-2:2020](https://pdfa.org/sponsored-standards/), at Section 7.3 Objects, provides the several PDF objects:

| Simple types                                   | Complex types                                     |
| ---------------------------------------------- | ------------------------------------------------- |
| Boolean: `true`, `false`                       | Array: `[549 3.14 false (Ralph) /SomeName]`       |
| Numeric: `+17`, `-98`, `+123.6`, `4.`, `-.002` | Dictionary: `<</Type 1 /SubType 2>>`              |
| String: `(This is a string)`, `<901FA3>`       | Stream                                            |
| Name: `/Name1`                                 | Indirect object definition: `12 0 obj ... endobj` |
| Null: `null`                                   | Indirect object reference: `12 0 R`               |

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

## Adding grammar

### Comments

```json
{
  "uuid": "e84e5061-3c27-4d2e-b0b6-9b9f1f12a687",
  "$schema": "https://raw.githubusercontent.com/martinring/tmlanguage/master/tmlanguage.json",
  "scopeName": "source.pdf",
  "name": "PDF",
  "patterns": [
    {
      "include": "#value"
    }
  ],
  "repository": {
    "value": {
      "comment": "PDF syntax",
      "patterns": [
        {
          "include": "#comment"
        }
      ]
    },
    "comment": {
      "name": "comment.line.percentage.pdf",
      "match": "(%)(.*)(?:\\r?\\n)",
      "captures": {
        "1": {
          "name": "punctuation.definition.comment.pdf"
        },
        "2": {
          "name": "comment.line.percentage.pdf"
        }
      }
    }
  }
}
```
