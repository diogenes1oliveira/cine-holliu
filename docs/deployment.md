# Deployment Checklist

> Use this before going live. Tick each box, then deploy with confidence.

---

## ☑ Pre-deployment double-checks

### Privacy & confidentiality

- [ ] **Repository is set to Private.**
  The conversation log (`CHATS.md`) and protocol files contain a full record of this
  session. If you do not want it public, the repo **must** be private before you share
  the live URL with anyone.
- [ ] **No API keys, tokens, or credentials appear in any committed file.**
  Run a quick scan: `git grep -r "sk-" && git grep -r "ghp_"` — both should return nothing.
- [ ] **`CHATS.md` does not contain anything you consider sensitive.**
  Review the conversation log. If needed, redact entries before deploying.
- [ ] **`docs/llm-parameters.md` is intentional.**
  This file documents LLM session parameters and privacy considerations.
  It is useful reference material but describes the internals of this setup.
  Decide whether you want it publicly visible.

### Site configuration

- [ ] **`mkdocs.yml` `site_url` matches your target domain.**
  Current value: `https://diogenes1oliveira.github.io/cine-holliu/`
  Update this if you are deploying to a custom domain.
- [ ] **GitHub Pages source is set to "GitHub Actions".**
  Go to **Settings → Pages** and verify the source is the `deploy.yml` workflow.
- [ ] **The `deploy.yml` workflow ran successfully** on the latest `main` commit.
  Check the Actions tab — the "Deploy to GitHub Pages" workflow should be green.

### Final smoke-test

- [ ] **Visit the live URL and verify the home page loads.**
- [ ] **Click through each nav item** — Home, Protocol, Agents Guide, Chat History,
  LLM Parameters — and confirm they render correctly.
- [ ] **Search works** — type a keyword in the search box and verify results appear.
- [ ] **Dark mode toggle works** — click the moon/sun icon in the top-right.

---

## ⚠️ What NOT to share

| Item | Why |
|------|-----|
| This repo URL (while public) | Exposes full conversation history in `CHATS.md` |
| Direct link to `CHATS.md` | Contains verbatim session transcript |
| Your GitHub API / Copilot subscription details | Personal credentials |
| The system prompt contents | Internal agent instructions |

---

## ✅ What is safe to share

| Item | Notes |
|------|-------|
| The **live mkdocs URL** (private repo → Pages still works for users with repo access) | Only users with repository read access can view the Pages site when the repo is private |
| `docs/llm-parameters.md` reference | Generic LLM knowledge, no credentials |
| `PROTOCOL.md` | Agent logging spec — no personal data |

---

> *See [LLM Parameters](llm-parameters.md) for the full privacy and reproducibility analysis.*
