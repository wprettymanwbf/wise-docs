<p align="center">
  <h1 align="center">WBF Internal Documentation</h1>
</p>

Welcome to the WBF (WBF.com) internal documentation and knowledge base repository. This repository contains all internal documentation, guides, and resources for the WBF team.

>**Note**: This repository uses [Git LFS](https://git-lfs.github.com/) (Large File Storage) for storing binary files such as images and `.gif`s. If you are contributing or updating images, please enable Git LFS per the instructions in the [Setup](#setup) section below.

## Table of Contents

- [About](#about)
- [Repository Structure](#repository-structure)
- [Getting Started](#getting-started)
  - [Setup](#setup)
  - [Cloning without binary files](#cloning-without-binary-files)
- [Contributing](#contributing)
- [Site Administration](#site-administration)
  - [Adding New Documentation](#adding-new-documentation)
  - [Organizing Content](#organizing-content)
  - [Building and Publishing](#building-and-publishing)
  - [Managing Images and Assets](#managing-images-and-assets)

## About

This repository serves as the central hub for WBF's internal documentation and knowledge base. Visit [WBF.com](https://wbf.com) for more information about our company.

## Repository Structure

The documentation is organized into the following main directories:

- **`docs/`** - Main documentation content, organized by topic
- **`api/`** - API documentation and technical references
- **`blogs/`** - Internal blog posts and announcements organized by year
- **`learn/`** - Learning resources and tutorials
- **`images/`** - Shared images and media assets
- **`templates/`** - Document templates for consistency
- **`build/`** - Build scripts and configuration

## Getting Started

### Setup

To contribute to this documentation:

1. Install [Git LFS](https://git-lfs.github.com/).
2. Run `git lfs install` to setup global git hooks. You only need to run this once per machine.
3. Clone the repository:
   - SSH: `git clone git@github.com:wprettymanwbf/wise-docs.git`
   - HTTPS: `git clone https://github.com/wprettymanwbf/wise-docs.git`
4. Now you can `git add` binary files and commit them. They'll be tracked in LFS.

### Cloning without binary files

You might want to clone the repo without downloading all images. Here are the steps:

1. Install [Git LFS](https://git-lfs.github.com/).
2. Run `git lfs install` to setup global git hooks. You only need to run this once per machine.
3. Clone the repo without binary files.
    - macOS / Linux:
      - SSH: `GIT_LFS_SKIP_SMUDGE=1 git clone git@github.com:wprettymanwbf/wise-docs.git`
      - HTTPS: `GIT_LFS_SKIP_SMUDGE=1 git clone https://github.com/wprettymanwbf/wise-docs.git`
    - Windows:
      - SSH: `$env:GIT_LFS_SKIP_SMUDGE="1"; git clone git@github.com:wprettymanwbf/wise-docs.git`
      - HTTPS: `$env:GIT_LFS_SKIP_SMUDGE="1"; git clone https://github.com/wprettymanwbf/wise-docs.git`
4. Now you can selectively checkout some binary files to work with. For example:
    - `git lfs pull -I "docs/getting-started"` to only download images in `docs/getting-started`
    - `git lfs pull -I "images"` to download all images in the `images` folder
    - `git lfs pull -I <PATTERN>`, as long as `<PATTERN>` is a valid [Git LFS Include and Exclude pattern](https://github.com/git-lfs/git-lfs/blob/main/docs/man/git-lfs-fetch.adoc#include-and-exclude).

## Contributing

We welcome contributions from all WBF team members! Here's how to contribute:

### Workflow

Two suggested workflows:

1. **For small changes**: Use the "Edit" button on each page to edit the Markdown file directly on GitHub.
2. **For significant changes**: Clone the repo and edit files locally. Use your preferred editor with Markdown preview support.

### Content Guidelines

- Write in clear, concise language
- Use consistent formatting and style
- Include relevant images and examples
- Keep documentation up-to-date
- Follow the existing document structure

## Site Administration

This section provides guidance on how to manage and maintain the documentation site.

### Adding New Documentation

1. **Choose the right location**:
   - General documentation → `docs/` folder
   - API documentation → `api/` folder
   - Blog posts/announcements → `blogs/YYYY/MM/DD/` folder structure
   - Learning materials → `learn/` folder

2. **Create your Markdown file**:
   - Use descriptive filenames (e.g., `getting-started.md`, `api-reference.md`)
   - Add frontmatter at the top of the file with metadata:
     ```yaml
     ---
     ContentId: unique-guid-here
     DateApproved: MM/DD/YYYY
     MetaDescription: Brief description for SEO
     ---
     ```

3. **Write your content**:
   - Use proper heading hierarchy (H1 for title, H2 for sections, etc.)
   - Include code examples in fenced code blocks with language specification
   - Add images to the appropriate `images/` subfolder within your section

4. **Commit and push your changes**:
   ```bash
   git add .
   git commit -m "Add documentation for [feature/topic]"
   git push
   ```

### Organizing Content

The documentation is organized hierarchically:

- **Main folders** represent major topic areas
- **Subfolders** organize related content
- **Index files** (`index.md`) serve as landing pages for each section
- **Images** should be stored in an `images/` subfolder within each section

Best practices:
- Keep related content together
- Use clear, descriptive folder and file names
- Maintain consistent structure across similar sections
- Update navigation/table of contents when adding new sections

### Building and Publishing

The documentation uses a static site generator pipeline:

1. **Local preview**: Use your editor's Markdown preview to review changes locally

2. **Build process**: The build pipeline is configured in `gulpfile.js` and includes:
   - Copying documentation files (`docs/`, `api/`, `blogs/`, etc.)
   - Processing assets and images
   - Generating the final site structure

3. **Publishing workflow**:
   - Create a pull request with your changes
   - Have your changes reviewed by team members
   - Once approved and merged, changes will be built and deployed
   - The automated pipeline handles the deployment process

4. **Build commands** (if running locally):
   ```bash
   npm install          # Install dependencies
   npm run lint         # Check for issues
   gulp build-dist      # Build the site (requires proper configuration)
   ```

### Managing Images and Assets

**Image Guidelines**:

1. **File format**:
   - Use PNG for screenshots and diagrams
   - Use JPEG for photos
   - Use GIF or MP4 for animations

2. **Storage**:
   - Store images in an `images/` subfolder within your content section
   - Use descriptive filenames (e.g., `configuration-dialog.png`)
   - Large binary files are tracked with Git LFS

3. **Adding images to documents**:
   ```markdown
   ![Descriptive alt text](images/filename.png)
   ```
   - Always include meaningful alt text
   - Use relative paths from your document

4. **Git LFS**:
   - All image files are automatically tracked by Git LFS
   - Ensure Git LFS is installed and configured (see [Setup](#setup))
   - Check that images are tracked: `git lfs ls-files`

**Asset Organization**:
- Keep assets close to the content that uses them
- Shared assets can go in the root `images/` folder
- Remove unused images to keep the repository clean

### Maintenance Tasks

**Regular maintenance**:
- Review and update outdated content quarterly
- Check for broken links using link checkers
- Archive old blog posts or announcements as needed
- Monitor repository size and clean up unused assets

**Troubleshooting**:
- If images don't appear, verify Git LFS is working: `git lfs env`
- For build issues, check `gulpfile.js` and ensure dependencies are installed
- For content issues, validate Markdown syntax and frontmatter format

---

For questions or support, please contact the documentation team or open an issue in this repository.
