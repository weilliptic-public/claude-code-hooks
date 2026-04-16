---
description: Install Weilliptic git hooks for commit-time receipt persistence
---

Install Weilliptic git hooks for the current project. This enables commit-time receipt persistence.

Run each of these bash commands:

```bash
# post-commit: persists the receipt ledger to Weilchain on every commit
printf '#!/bin/sh\n${CLAUDE_PLUGIN_ROOT}/bin/git-commit-hook\n' > .git/hooks/post-commit
chmod +x .git/hooks/post-commit
```

```bash
# Initialize the .weilliptic receipt ledger if it doesn't exist yet
mkdir -p .weilliptic
[ -f .weilliptic/.receipts ] || printf 'branch:%s\nprompt_offset:0\n' "$(git rev-parse --abbrev-ref HEAD)" > .weilliptic/.receipts
grep -qxF '.weilliptic/' .gitignore 2>/dev/null || echo '.weilliptic/' >> .gitignore
```

After these commands complete, Weilliptic will automatically persist audit receipts to Weilchain on every `git commit`.
