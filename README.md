# macos-skill-test

Run agent-skill tests on a **real macOS machine, for free, programmatically** — no local VM, no Mac purchase.

Uses GitHub-hosted `macos-15` runners. Public repositories get **unlimited free Actions minutes** (macOS included), so every run costs $0.

## Automated run (recommended)

1. Actions → **macOS Skill Test** → **Run workflow**
2. The job runs the zlog skill suites (`test-posix.sh`, `test-install.sh`) plus system info on Apple silicon macOS.
3. A report is committed to [`results/`](./results) and uploaded as a workflow artifact.

CLI equivalent:

```sh
gh workflow run "macOS Skill Test" -R sebin-gg/macos-skill-test
gh run watch -R sebin-gg/macos-skill-test
```

## Interactive session (SSH / web shell)

To get a hands-on macOS shell over the web, run the workflow with the
`interactive` input checked. It starts a [tmate](https://tmate.io) session;
the SSH command and a **web-shell link** appear in the job log within ~30s.

- SSH: `ssh <tmate-ssh-string-from-log>` (no key needed, ephemeral)
- Web: open the `https://tmate.io/...` URL printed in the log
- Exit the shell to end the job (or let the 6h job limit expire)

The session is ephemeral: the VM is destroyed when the job ends. Never put
secrets you care about into it.

## Cost

| Item | Cost |
| --- | --- |
| Public-repo macOS minutes | $0 (free allowance) |
| tmate relay | $0 |
| Local disk / VM images | $0 (nothing installed locally) |
