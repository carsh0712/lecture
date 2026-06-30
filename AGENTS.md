# AGENTS.md

## Project Structure

This repository keeps HTML manuals under the `html/` directory.

Use this structure for Naver-related manuals:

```text
html/
  naver/
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

- Create one top-level directory per service under `html/`.
- For Naver manuals, use `html/naver/` as the root.
- `html/naver/index.html` is the Naver manual landing page.
- Links from `html/naver/index.html` should be organized by chapter.
- Each chapter can contain multiple page HTML files.
- Each linked manual page should live directly under its chapter directory as `<section-id>-<page-slug>.html`.
- Do not create an extra page directory just to hold `index.html`; `file-name.html` is enough.
- Put chapter or page-specific assets inside that chapter's `assets/` directory when needed.
- Use the section id, then a lowercase hyphen-separated file name, such as `0-overview.html`, `1-account-login.html`, or `e1-nodejs-install.html`.
- The prefix at the front is the section id inside the chapter, not the chapter number.
- Prefer relative links so the manual can be opened locally or served statically.
- Link directly to the `.html` file instead of only linking to a directory path. Local browsers may show a file listing when a directory path is opened.

## Naver Manual Menu

The Naver manual sidebar is organized by chapters.

Current chapter structure:

```text
0. AI 사용하기
   - 개요
   - Claude Desktop과 Claude Code CLI 이해하기
   - Node.js 설치하기
   - Confluence에 작성하기
   - HTML로 n3r 배포하기
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
html/naver/using-ai/
```

Example links from a chapter group:

```html
<p class="manual-chapter">AI 사용하기</p>
<a href="./using-ai/0-overview.html">개요</a>
<a href="./using-ai/e2-claude-code-basics.html">Claude Desktop과 Claude Code CLI 이해하기</a>
<a href="./using-ai/e1-nodejs-install.html">Node.js 설치하기</a>
<a href="./using-ai/1-1-confluence.html">Confluence에 작성하기</a>
<a href="./using-ai/1-2-html-n3r-deploy.html">HTML로 n3r 배포하기</a>
```

## Naver Manual Audience

The Naver manual is educational material for planners, product managers, and other non-developer stakeholders who may not be familiar with implementation details.

Writing rules for this audience:

- Explain concepts in plain Korean before using technical terms.
- Avoid assuming prior development knowledge.
- When a technical term is necessary, add a short practical explanation.
- Prefer workflow, purpose, decision context, and expected result over implementation details.
- Include enough background for a planner or PM to understand why a step matters.
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
    <title>Naver Manual</title>
    <link rel="stylesheet" href="./assets/css/styles.css">
  </head>
  <body>
    <div class="manual-layout">
      <nav class="manual-sidebar" aria-label="Manual navigation">
        <a href="./index.html">Naver Manual</a>
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
- Write for planners and PMs who may not know development concepts well.
- Organize instructions as numbered steps.
- Put warnings, prerequisites, and important notes near the related step.
- Keep each page focused on one task or topic.
- Use screenshots only when they clarify a step.
- Ensure all internal links continue to work when opening files directly from disk.
