# Codex-Style Code Reviews for Gemini CLI & Claude Code

Bring OpenAI Codex's structured code review prompts to [Gemini CLI](https://github.com/google-gemini/gemini-cli) and [Claude Code](https://docs.anthropic.com/en/docs/claude-code).

What I like about Codex reviews is the strict bug categorization (P0-P3) and focus on actionable findings. The default chat in these tools doesn't have that structure, so I ported the prompts over as slash commands.

<img width="1380" height="419" alt="sample-review" src="https://github.com/user-attachments/assets/c3ad4b81-c8a0-435e-933c-0a274226375b" />

## Source

These commands are based on the review prompts from the OpenAI Codex repository:

- [review_prompts.rs](https://github.com/openai/codex/blob/main/codex-rs/core/src/review_prompts.rs) - Review target types and prompt generation
- [review_prompt.md](https://github.com/openai/codex/blob/main/codex-rs/core/review_prompt.md) - Guidelines and priority system

The output format is adapted from JSON to Markdown so it renders properly in the terminal.

## Installation

### Gemini CLI

1. Install Gemini CLI if you haven't:
   ```bash
   npm install -g @google/gemini-cli@latest
   ```

2. Copy the command files:
   ```bash
   mkdir -p ~/.gemini/commands/review
   cp gemini/review.toml ~/.gemini/commands/
   cp gemini/review/*.toml ~/.gemini/commands/review/
   ```

### Claude Code

1. Install Claude Code if you haven't:
   ```bash
   npm install -g @anthropic-ai/claude-code@latest
   ```

2. Copy the command files:
   ```bash
   mkdir -p ~/.claude/commands/review
   cp claude/review.md ~/.claude/commands/
   cp claude/review/*.md ~/.claude/commands/review/
   ```

## Usage

### Gemini CLI

**Review uncommitted changes**
```
/review
```

**Review against a branch**
```
/review:branch main
```

**Review a specific commit**
```
/review:commit a1b2c3d
```

### Claude Code

**Review uncommitted changes**
```
/review
```

**Review against a branch**
```
/review:branch main
```

**Review a specific commit**
```
/review:commit a1b2c3d
```

## Disclaimer

Not affiliated with OpenAI, Google, or Anthropic. Just a set of custom commands using public prompt techniques.
