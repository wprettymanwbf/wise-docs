# WBF Internal Documentation

Welcome to the WBF internal documentation repository!

## Contribute to WBF documentation

Thank you for your interest in contributing to WBF's internal documentation!

* [Contributing](#contributing)
* [Documentation intent](#documentation-intent)
* [Repository organization](#repository-organization)
* [Authoring Tools](#authoring-tools)
* [How to use Markdown to format your topic](#how-to-use-markdown-to-format-your-topic)
* [Topic Metadata](#topic-metadata)
* [Formatting](#formatting)

## Contributing

To contribute to WBF documentation, you can either:

1. **Small changes**: Edit files directly on GitHub using the "Edit" button
2. **Larger changes**: Fork this repository and submit a pull request

* [How to fork a repository](https://docs.github.com/get-started/quickstart/fork-a-repo)
* [How to make a pull request](https://docs.github.com/pull-requests/collaborating-with-pull-requests/proposing-changes-to-your-work-with-pull-requests/creating-a-pull-request)
* [Changing a commit message](https://docs.github.com/pull-requests/committing-changes-to-your-project/creating-and-editing-commits/changing-a-commit-message)
* [How to squash commits](https://docs.github.com/pull-requests/collaborating-with-pull-requests/incorporating-changes-from-a-pull-request/about-pull-request-merges#squash-and-merge-your-commits)

The wise-docs repository supports [Git LFS](https://git-lfs.github.com/) for managing large binary files. See the [README](README.md#getting-started) section for details on enabling Git LFS for your local repository.

## Documentation intent

The goal of WBF's internal documentation is to provide clear, comprehensive information about company systems, processes, and best practices.

The documentation should:

* Be accurate and up-to-date
* Be easy to understand and navigate
* Provide practical guidance and examples
* Support both new and experienced team members
* Cover technical and non-technical topics relevant to WBF

## Repository organization

This repository contains the following top-level folders:

* `api/` - API documentation and technical references
* `blogs/` - Company blog posts and announcements organized by date
* `build/` - Build scripts and configuration files
* `docs/` - Main documentation organized by topic
* `images/` - Shared images and assets
* `learn/` - Learning resources, tutorials, and training materials
* `release-notes/` - Software release notes and changelogs (if applicable)
* `templates/` - Document templates for consistency

Within these folders, you'll find Markdown files for content. Many folders also contain an `images/` subfolder for section-specific images and screenshots.

### Branches

We recommend that you create local working branches that target a specific scope of change (and then submit a pull request when your changes are ready). Each branch should be limited to a single concept/topic, both to streamline workflow, and to reduce the possibility of merge conflicts.  The following efforts are of the appropriate scope for a new branch:

* A new topic (and associated images).
* Spelling and grammar edits on a topic.
* Applying a single formatting change across a large set of topics.

## Authoring tools

You can use any Markdown editor to write documentation. Some popular options include:

* [Visual Studio Code](https://code.visualstudio.com) - A free, powerful code editor with excellent Markdown support
* [Typora](https://typora.io/) - A minimal Markdown editor
* GitHub's built-in editor for quick changes

## How to use Markdown to format your topic

The topics in this repository use Markdown.  Here is a good overview of [Markdown basics](https://docs.github.com/get-started/writing-on-github/getting-started-with-writing-and-formatting-on-github/basic-writing-and-formatting-syntax).

## Topic Metadata

Topic metadata enables certain functionalities for the topics such as topic description and online search optimization.

The page title is taken from the first H1 heading in the topic.

* **ContentId** - A GUID that uniquely identifies the topic to DevDiv doc reporting.
* **DateApproved** - The date of the most recent update or review. It is displayed at the bottom of an article to indicate freshness. The date should be updated in a significant PR.
* **MetaDescription** - The meta description for this page, which helps for search. Use sentence structure limited to 300 characters.
* **MetaSocialImage** - Optional. Used for og:image in page header for sharing on social media. Should be 1024 x 512 .png.
* **MetaTags** - Optional. Further tags for this page again for search.

## Table of contents

The table of contents (TOC) is defined in the `/docs/toc.yml` file. The TOC is used to generate the left rail navigation for the documentation. If a topic is not listed in the `/docs/toc.yml` file, it will not be included in the left rail navigation.

To add a new topic to the TOC, add a new entry in the `topics` attribute of the appropriate section in the `/docs/toc.yml` file. The TOC is organized into sections, each with a name and an area. The area is used to group related topics together.

The order in which the topics are listed in the `/docs/toc.yml` file determines the order in which they are displayed in the left rail navigation.

Each topic in the TOC has two attributes:

* TOC title: the title that is displayed in the left rail navigation.
* File name: the relative path to the topic file in the format `/docs/<subfolder>/<filename-without-md>`.

The following example shows a `Getting Started` section that has two topics.

```yaml
    {
      "name": "Getting Started",
      "area": "getstarted",
      "topics": [
        ["Company Overview", "/docs/getting-started/overview"],
        ["Tools and Systems", "/docs/getting-started/tools"]
      ]
    },
```

To create a subsection within a section, add a subsection entry to the `topics` attribute. A subsection entry has the following attributes:

* TOC Title: empty string
* File name: empty string
* Subsection: a subsection entry with the same format as a section entry. It has a `name` attribute, an `area` attribute, and a `topics` attribute.

The following example shows a `Guides` subsection with two topics, within the `GitHub Copilot` section.

```yaml
    {
      "name": "Development",
      "area": "development",
      "topics": [
        ["Overview", "/docs/development/overview"],
        ["Best Practices", "/docs/development/best-practices"],
        ["", "", {
          "name": "Guides",
          "area": "development/guides",
          "topics": [
            ["Setup Guide", "/docs/development/guides/setup"],
            ["Testing Guide", "/docs/development/guides/testing"]
          ]
        }
        ],
        ["FAQ", "/docs/development/faq"]
      ]
    },
```

## Product/Company Name

When referring to the company:
* Use "WBF" or "WBF.com" consistently
* Avoid informal variations unless contextually appropriate

### Metadata for /api docs

**For Writer**:

* **MetaDescription** - The meta description for this page, which helps for search.

**For Doc Maintainer**:

* **DateApproved** - This is set when the page is published or last reviewed.

## File and Folder names

Use lowercase for file and folder names and dashes `-` as separators.

For example:

* `/docs/editor/workspace-trust.md`
* `/docs/supporting/troubleshoot-terminal-launch.md`
* `/api/extension-guides/custom-editors.md`

### Moving or renaming content

Before moving or renaming content, a redirect should be added in case people have bookmarked the topic. Redirects are added in the private website repo.

It seems to improve CSAT if, when a topic title or intent is changed, the filename is also updated. resulting in a new, more appropriate URL.

For example: `/docs/editor/extension-gallery.md` -> `/docs/configure/extensions/extension-marketplace.md`

### sitemap

The sitemap is authored in `/build/sitemap.xml` and should be updated when new topics are added or existing content moved or renamed.

## Formatting

### Headings & Right Nav

H2 subheadings `##` end up in the right-hand jump list for the document (the jump list is created by our compile script).  It's a good idea to include h2 subheadings to help users get an overview of the doc and quickly navigate to the major topics.

### Text formatting

Use bold for commands and UI elements.

    **File: Open Folder**
    **Settings Panel**

Limit the use of bold for emphasis unless it is crucial to get the user's attention. Avoid the use of italics for emphasis since it may not render well in all contexts.

Use inline code formatting (backticks) for settings, filename, and JSON attributes.

    `files.exclude`
    `tasks.json`
    `preLaunchTask`

Use '>' to show menu sequence.

    **File** > **Preferences** > **Settings**
    **View** > **Command Palette**

### Links

For links within our own documentation, use a site relative link like `/docs/editing/codebasics.md`.

>For example: `[Why VS Code](/docs/editor/whyvscode.md)` - links to the **Why Visual Studio Code** page

>**Note:** For navigation on GitHub, you should add the .md suffix.  The suffix is removed during conversion to HTML.

### Bookmarks

To provide links to h2 subheadings (Markdown ##), the format is `[Link Text](page.md#subheading-title)`.

Note the subheading title is lowercase and subheading title words are separated by '-' hyphens.

>For example: `[Keyboard Shortcuts](/docs/editing/codebasics.md#keyboard-shortcuts)` - links to https://code.visualstudio.com/docs/editing/codebasics#_keyboard-shortcuts.

### Images

Images are important to bring the product to life and clarify the written content.

* Store images for an article in the `docs/<section>/images/<article name>` subfolder. For example: `docs/sourcecontrol/images/overview`.

* Image filenames should use all lowercase and use dashes (`-`) as word separator. For example: `![Debug Breakpoints](images/debugging/breakpoints-view.png)`

* Link to an image using relative path names, the path and filename are case-sensitive.

* Images are cached on the server for indeterminate time, so don't update images in-place. Create a new file and add a version indicator (yyyymmddseq) to the image filename. 

> [!IMPORTANT]
> Make sure you have Git LFS enabled on your machine!

### Key bindings

The VS Code website is able to show the correct key bindings depending on the reader's operating system (macOS, Windows, or Linux).

To enable this for keyboard shortcuts, use the format `kb(workbench.action.files.openFile)` where the command identifier is included in parentheses.

>For a list of key bindings and the relevant `Command Ids`, review the [key bindings document](https://code.visualstudio.com/docs/getstarted/keybindings#_default-keyboard-shortcuts).

If you are listing out multiple key bindings, you can use a table.

>Shortcut|Key Strokes
>--------|-----------
>Cut|`kb(editor.action.clipboardCutAction)`
>Copy|`kb(editor.action.clipboardCopyAction)`
>Paste|`kb(editor.action.clipboardPasteAction)`

### Source Code

For source code, we use the fenced code block notation ```` ``` ````.

>**Note:** You can add an optional language identifier to enable syntax highlighting in your fenced code block. For example, ```` ```json ```` or ```` ```javascript ````. [Read more →](https://docs.github.com/get-started/writing-on-github/working-with-advanced-formatting/creating-and-highlighting-code-blocks#syntax-highlighting)

An example of JavaScript source code:

```javascript
function fancyAlert(arg) {
  if (arg) {
    $.facebox({ div: foo });
  }
}
```

## Gotchas

### Double opening curly braces break generated handlebar files

Escape double opening curly braces in code blocks.

```html
<!DOCTYPE html>
<html>
    <head>
        <meta charset="utf-8" />
        <title>Hello, Flask</title>
    </head>
    <body>
        <strong>Hello there, \{{ name }}!</strong> It's \{{ date.strftime("%A, %d %B, %Y at %X") }}.
    </body>
</html>
```
