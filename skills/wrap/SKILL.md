---
name: wrap
description: wrap up work, commit with a reasonable summary message, push
---

## steps

1. take parameter repo name, find repo in the workspace
1. add unstaged changes (use repo context to decide which ones to exclude, for example, hidden folder or cache files)
1. check trailing whitespace `git diff --check && git diff --cached --check`
1. summarize changes in one sentence less than 10 words
1. commit with the message and push
