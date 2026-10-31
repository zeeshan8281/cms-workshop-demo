# Papertrail CMS

A small, browser-local content management system for the High on AI workshop. One editable HTML file, with an editor dashboard, draft preview and a reader view.

## Clone and run

This repository is private, so clone with a GitHub account that has access.

```bash
git clone https://github.com/zeeshan8281/cms-workshop-demo.git
cd cms-workshop-demo
python3 -m http.server 8000 --bind 127.0.0.1
```

Open **http://127.0.0.1:8000**. Leave the terminal running; press `Ctrl+C` to stop it. On Windows with the Python launcher installed, use `py -m http.server 8000 --bind 127.0.0.1` instead. If port 8000 is busy, use 8001 in both the command and the browser URL.

There is no build step or package installation. If Python is unavailable, opening `index.html` directly may work for basic interaction, but `file:` storage behavior varies across browsers and that mode has not been browser-tested. Prefer localhost for persistence checks. This development server is not production hosting.

## Try the CMS

1. Click **New post**, enter a title and body, and save a draft.
2. Edit the suggested slug and category if needed. Slugs must be unique across all posts.
3. Use **Preview** to inspect draft or unsaved text without publishing it.
4. Click **Publish locally**, then **Reader view** to read the published post.
5. **Update locally** updates an already-published post. **Unpublish locally** removes it from the reader while retaining the draft.
6. Search or filter the content list, then refresh to check persistence.

Three fictional sample posts are included. Post bodies are plain text, not HTML or Markdown.

## What local publishing means

**Publish locally changes this browser's reader view only. It does not deploy anything to the internet.** There is no backend, authentication, private-draft protection or cross-device sync. Draft status is a display filter, not a security boundary. Do not enter sensitive or irreplaceable content.

Posts are saved in `localStorage` when available. Changing browser, origin or port can show a different dataset. Browser cleanup or storage restrictions can remove or prevent saving. A visible warning explains memory-only mode. Use one tab at a time.

## Files

- `index.html`: complete app, including CSS, JavaScript and sample content
- `workshop_prompts.txt`: plan, small build, test, improve and review prompts
- `.gitignore`: excludes common local files and secrets

## Verification

Core flows were tested in Chromium on a local preview: draft creation and edits, validation, unique normalized slugs, preview, publishing, reader navigation, published updates, unpublishing, search/filtering, reload persistence, unsaved-change safeguards and literal text rendering. Storage-failure branches were checked with mocked logic tests.

Direct-file mode, other browsers, real phones, narrow layouts and a full accessibility audit were not browser-tested. This is a workshop prototype, not a production-ready CMS. A real multi-user service needs authentication/permissions, a database, backups and secure hosting.
