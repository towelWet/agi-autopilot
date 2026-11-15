# agi-autopilot

AGI-style autopilot mode for AI IDE agents. When activated, the agent works autonomously
through multi-step tasks without stopping for confirmation on every action.

## Use

```text
/agi-autopilot
```

Other triggers: "autopilot mode", "just do it", "stop asking", "keep going", "don't stop",
"full auto", "agentic mode".

The agent acknowledges with one line, then starts working:

```text
Autopilot on. Working through the task now.
```

## Loop protocol

| Step | Action |
|---|---|
| Run | execute best matching build command |
| Log | capture full output to timestamped log file |
| Inspect | identify first real error; ignore cascading errors |
| Fix | smallest, reversible fix for that error |
| Repeat | restart loop immediately |

## Decision framework

| Question | Yes | No |
|---|---|---|
| Destructive (delete files, overwrite data, install packages)? | ask user | just do it |
| Ambiguous requirement? | pick most likely, state assumption, continue | just do it |
| Tried this exact approach and failed? | switch strategy | try it |
| Genuinely stuck, no path forward? | ask user with specific question + what was tried | keep working |

## Install

Place this folder at `~/.claude/skills/agi-autopilot/`.

## Files

| File | Purpose |
|---|---|
| `SKILL.md` | the skill |
