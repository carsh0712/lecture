# AGENTS.md

## Project Structure

This repository keeps HTML manuals under the `docs/` directory.

Use this structure for Four Leaf Clover-related manuals:

```text
docs/
  four-leaf-clover/
    index.html
    assets/
      css/
        styles.css
    <chapter-slug>/
      <section-id>-<page-slug>.html
      assets/
        images/
        css/
        js/
```

Rules:

- Create one top-level directory per service under `docs/`.
- For Four Leaf Clover manuals, use `docs/four-leaf-clover/` as the root.
- `docs/four-leaf-clover/index.html` is the Four Leaf Clover manual landing page.
- Links from `docs/four-leaf-clover/index.html` should be organized by chapter.
- Each chapter can contain multiple page HTML files.
- Each linked manual page should live directly under its chapter directory as `<section-id>-<page-slug>.html`.
- Do not create an extra page directory just to hold `index.html`; `file-name.html` is enough.
- Put chapter or page-specific assets inside that chapter's `assets/` directory when needed.
- Use the section id, then a lowercase hyphen-separated file name, such as `0-overview.html`, `1-account-login.html`, or `e1-nodejs-install.html`.
- The prefix at the front is the section id inside the chapter, not the chapter number.
- Prefer relative links so the manual can be opened locally or served statically.
- Link directly to the `.html` file instead of only linking to a directory path. Local browsers may show a file listing when a directory path is opened.

## Four Leaf Clover Manual Menu

The Four Leaf Clover manual sidebar is organized by chapters.

Current chapter structure:

```text
0. 문서 작성과 배포
   - 개요
   - Claude Desktop과 Claude Code CLI 이해하기
   - Confluence에 작성하기 (수정예정)
   - HTML로 클라우드 서버 배포하기
   - 클라우드 서버 앱 생성 (수정예정)
   - CLAUDE.md 파일의 역할 (수정예정)
1. 설치 가이드
   - Node.js 설치하기 (수정예정)
   - Git 설치 가이드 (수정예정)
   - GQuery MCP 서버 설치 (수정예정)
   - Atlassian MCP 서버 설치 (수정예정)
```

Rules:

- Treat each chapter as a large sidebar menu group.
- A chapter can contain multiple child pages.
- Do not create child pages until the manual content has been discussed and confirmed.
- When a child page is added, place it under the chapter directory.
- Use a Korean chapter title in the visible sidebar label.
- Use a lowercase English slug for the directory name.

Recommended directory names:

```text
docs/four-leaf-clover/using-ai/
docs/four-leaf-clover/install-guide/
```

Example links from a chapter group:

```html
<p class="manual-chapter">문서 작성과 배포</p>
<a href="./using-ai/0-overview.html">개요</a>
<a href="./using-ai/e2-claude-code-basics.html">Claude Desktop과 Claude Code CLI 이해하기</a>
<a href="./using-ai/1-1-confluence.html">Confluence에 작성하기 (수정예정)</a>
<a href="./using-ai/1-2-html-CloudServer-deploy.html">HTML로 클라우드 서버 배포하기</a>
<a href="./using-ai/1-4-CloudServer-app-create.html">클라우드 서버 앱 생성 (수정예정)</a>
<a href="./using-ai/1-5-claude-md-role.html">CLAUDE.md 파일의 역할 (수정예정)</a>

<p class="manual-chapter">설치 가이드</p>
<a href="./install-guide/e1-nodejs-install.html">Node.js 설치하기 (수정예정)</a>
<a href="./install-guide/e6-git-install-guide.html">Git 설치 가이드 (수정예정)</a>
<a href="./install-guide/e3-cquery-mcp-install.html">GQuery MCP 서버 설치 (수정예정)</a>
<a href="./install-guide/e4-atlassian-mcp-install.html">Atlassian MCP 서버 설치 (수정예정)</a>
```

## Four Leaf Clover Manual Audience

The Four Leaf Clover manual is educational material for non-developers who may not be familiar with implementation details.

Writing rules for this audience:

- Explain concepts in plain Korean before using technical terms.
- Avoid assuming prior development knowledge.
- When a technical term is necessary, add a short practical explanation.
- Prefer workflow, purpose, decision context, and expected result over implementation details.
- Include enough background for non-developers to understand why a step matters.
- Keep examples close to real planning, content review, product operation, or collaboration scenarios.

## HTML Layout

All manual pages should use a consistent two-column layout:

- A left sidebar for navigation between manual pages.
- A main content area for the selected manual content.

Basic layout requirements:

- The sidebar should appear on the left on desktop screens.
- The sidebar should contain a dashboard link and chapter groups.
- Page links should appear as children under their related chapter.
- The current page link should be visually distinguishable.
- The main content area should contain the page title, overview, steps, notes, and any screenshots or examples.
- Keep navigation labels short and scannable.
- Use semantic HTML elements such as `nav`, `main`, `section`, `h1`, `h2`, `ol`, and `ul`.
- Keep CSS shared where practical, but avoid introducing a build step unless the project later requires one.

Recommended page skeleton:

```html
<!doctype html>
<html lang="ko">
  <head>
    <meta charset="utf-8">
    <meta name="viewport" content="width=device-width, initial-scale=1">
    <title>Four Leaf Clover Manual</title>
    <link rel="stylesheet" href="./assets/css/styles.css">
  </head>
  <body>
    <div class="manual-layout">
      <nav class="manual-sidebar" aria-label="Manual navigation">
        <a href="./index.html">Four Leaf Clover Manual</a>
        <a href="./0-overview.html">Overview</a>
      </nav>

      <main class="manual-content">
        <h1>Page Title</h1>
        <section>
          <h2>Overview</h2>
          <p>Write the purpose of this manual page here.</p>
        </section>
      </main>
    </div>
  </body>
</html>
```

## Writing Guidelines

- Write manual content in Korean unless a term is normally used in English.
- Write for non-developers who may not know development concepts well.
- Organize instructions as numbered steps.
- Put warnings, prerequisites, and important notes near the related step.
- Keep each page focused on one task or topic.
- Use screenshots only when they clarify a step.
- Ensure all internal links continue to work when opening files directly from disk.
