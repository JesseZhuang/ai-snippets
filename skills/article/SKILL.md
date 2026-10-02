---
name: article
description: Write Astro blog posts
---

This [blog post](../../../astro-leet/src/data/blog/design-how-tidb-tso-works.md) is a good exmaple of database learning article I would like to write.

Another good [example](../../../astro-leet/src/data/blog/aiml-generative-ai-large-language-models-1.md) about AI.

for git operations, see [token path](../../config/pat.path.md)

## git rules

- Commit directly on the repo's default branch (`main`). Never create a feature/topic branch (e.g. `codex/...`, `blog/...`) and never open a pull request.
- Before committing: `git fetch origin && git rebase origin/main` so the push is a fast-forward.
- Push with `git push origin main`. If the push is rejected as non-fast-forward, fetch, rebase again, and retry. Never force-push.
- Leave the checkout on `main` when done.

save logs of the workflow in /tmp/blog-article-<date and time>

## workflow

1. this skill should write two blog posts, see below
1. for the first blog post, pick a topic that is not in astro-leet repo. The technology should be well-known in the industry. Current topics include databases, machine learning/artificial intelligence, system design. Choose something that is worth to share and learn about.
1. for the second blog post, pick a topic or source code for TiDB that has not been covered before, the post should focus on helping the readers understanding how tidb source code works, how the different classes, packages, components work together (generate component diagram or UML sequence diagram ); what are some important configs. scope should be small. focus on one to five classess for one post. search tidb public doc and internet posts to help as well. focus on github repos include pingcap/tidb and tikv/tikv.
1. Write posts discussing key details, how does different pieces of code work toegether. Use language that a fresh college graduate can understand. Structure parts as story-like if possible.
1. draw diagrams with pure ascii as needed
1. point to source code where ncecessary
1. include references
1. commit on `main` and push to `origin main` (see git rules above; no feature branch)
