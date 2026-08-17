# hello-world-demo

Demo repository for the workflow board. Runner-launched Claude Code sessions run headless
(`--permission-mode acceptEdits`), which denies `gh` and `git` by default; the committed
`.claude/settings.json` allows both in this repository only.

A committed allow-rule is not sufficient on its own. Claude Code ignores `permissions.allow` from an
untrusted workspace, logging:

```
Ignoring 1 permissions.allow entry from .claude/settings.json: this workspace has not been trusted.
```

The workspace also needs `projects["<repo path>"].hasTrustDialogAccepted: true` in the host's
`~/.claude.json`. Trust is keyed on the **repository** path, not the per-card worktree, so it is set
once per repo rather than once per run.
