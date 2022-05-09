---
title: "Getting Started With Markdown"
description: Markdown is a plain text format for writing structured documents. 
date: 2021-07-24T10:00:00+01:00
draft: false
toc: true
pinned: false
featuredImage: ''
tags: [Markdown, VSCode]
categories: [Documentation]
series: [Markdown]
---

Markdown is a plain text format for writing structured documents.  Writing Markdown is a great way to take notes, the author spends less time distracted by formatting and more time focusing on content.

<!--more-->

To get started with Markdown create a plain text file. Markdown documents are identified with the file extension '.md', so if your new file ends with '.txt', change it to '.md'.

Markdown files can be edited with any text editor.  Apps such as Notepad or Wordpad are suitable.  Text editor apps won't help you though while editing your Markdown files.  The light-weight IDE, [VSCode](https://code.visualstudio.com/) has built-in support for Markdown, without the need to install extensions.

The [original specification of Markdown](https://daringfireball.net/projects/markdown/syntax), by John Gruber and Aaron Swartz, dates from 2004.  The specification has been interpreted differently since then, leading to many implementations.  There are now many variations of Markdown.

## CommonMark

The [CommonMark](https://commonmark.org/) project describes itself as being "A strongly defined, highly compatible specification of Markdown".  Multiple applications and frameworks now work to the CommonMark specification.  CommonMark is also the stated direction of [GitHub](https://github.blog/2017-03-14-a-formal-spec-for-github-markdown/) and is the specification used by [VSCode](https://code.visualstudio.com/docs/languages/markdown#_does-vs-code-support-github-flavored-markdown).

## Markdown Tutorial

Here's an example of a Markdown document:

```markdown
# This is a Level 1 Heading

This is plan text. Here is a word in **bold**. An example of *italic*.

## A Level 2 Heading
Some text here with a link to [this site](https://example.com).

### A Level 3 Heading

Numbered lists are supported:

1. this is the first item
1. here's the second
1. and the third

Tables are also supported:

| Animal | Sound |
|--------|-------|
| Dog    | woof  |
| Cow    | moo   |
```

## Code Blocks and Syntax Highlighting

Code blocks begin and end with three backticks, like this:

\` \` \`

\` \` \`

To add syntax highlighting, include the name of the language at the start of the code block, such as:

\` \` \` Rust

\` \` \`

## Online Tutorial

The [60 Second Tutorial](https://commonmark.org/help/) is a great place to start.

## Resources of Interest

1. [highlight.js](https://highlightjs.org/static/demo/) for a list of languages available to add to code blocks.
1. [Tables Generator](https://www.tablesgenerator.com/markdown_tables) is a fast way of creating tables and supports pasting data copied from spreadsheets, docs and other sources.
1. [VSCode](https://code.visualstudio.com/) is free, open source and widely used.  Great for editing Markdown, also languages such as Python, Rust, C++. The [preview pane](https://code.visualstudio.com/docs/languages/markdown#_markdown-preview) provides instant feedback on how your document looks. Shortcut to enable preview: <kbd>Ctrl</kbd> + <kbd>K</kbd> <kbd>V</kbd>.
1. [Code Spell Checker](https://marketplace.visualstudio.com/items?itemName=streetsidesoftware.code-spell-checker), extension for VSCode, is a general spell checker. Great for spell checking source code comments and Markdown documents.
1. [Markdown PDF](https://marketplace.visualstudio.com/items?itemName=yzane.markdown-pdf), extension for VSCode,  generates PDF and HTML versions of the currently edited Markdown file.
1. [Pandoc](https://pandoc.org/) is a super powerful open-source utility that converts docs in various formats to many other formats.  Excellent for converting Markdown to .epub format, .docx and many other formats.