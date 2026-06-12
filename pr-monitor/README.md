# pr-monitor

Monitor GitHub PR checks and get notified when they complete.

## Features

- Polls PR checks every 5 minutes (configurable)
- Desktop notifications on pass/fail
- Terminal output with timestamps
- Shows breakdown of pending, passed, failed, and skipped checks
- Prints helpful commands (approve, open in browser) when done

## Requirements

- `gh` CLI installed and authenticated
- `jq` for JSON parsing
- Desktop notification support (Linux: `notify-send`, macOS: built-in, etc.)

## Usage

Monitor a PR by URL:
```bash
pr-monitor https://github.com/owner/repo/pull/123
```

Monitor a PR by number with repo flag:
```bash
pr-monitor 123 --repo owner/repo
```

## Options

- `--repo owner/repo` — Repository in `owner/repo` format (required if using PR number)

## Environment

- `PR_MONITOR_INTERVAL` — Polling interval in seconds (default: 300)

```bash
PR_MONITOR_INTERVAL=60 pr-monitor 123 --repo owner/repo
```

## Example Output

```
[14:23:15] PR #123 monitor started
[14:23:22] total=5 pending=3 pass=0 fail=0 neutral=2
[14:28:32] total=5 pending=0 pass=4 fail=1 neutral=0
✅ PR #123 PASSED
```

When checks complete, the script exits and offers commands to approve or view the PR.
