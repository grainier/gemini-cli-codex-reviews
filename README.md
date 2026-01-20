# Codex-Style Reviews for Gemini CLI

Bring OpenAI Codex's structured code review prompts to [Gemini CLI](https://github.com/google-gemini/gemini-cli).

What I like about Codex reviews is the strict bug categorization (P0-P3) and focus on actionable findings. The default Gemini chat doesn't have that structure, so I ported the prompts over as slash commands.

## Source

These commands are based on the review prompts from the OpenAI Codex repository:

- [review_prompts.rs](https://github.com/openai/codex/blob/main/codex-rs/core/src/review_prompts.rs) - Review target types and prompt generation
- [review_prompt.md](https://github.com/openai/codex/blob/main/codex-rs/core/review_prompt.md) - Guidelines and priority system

The output format is adapted from JSON to Markdown so it renders properly in the terminal.

## Installation

1. Install Gemini CLI if you haven't:
   ```bash
   npm install -g @google/gemini-cli@latest
   ```

2. Create the commands directory and copy the files:
   ```bash
   mkdir -p ~/.gemini/commands/review
   cp review.toml ~/.gemini/commands/
   cp review/*.toml ~/.gemini/commands/review/
   ```

## Usage

**Review uncommitted changes**

Check your staged and unstaged work before committing:
```
/review
```

**Review against a branch**

Compare your current HEAD against a base branch. Calculates the merge-base automatically:
```
/review:branch main
```

**Review a specific commit**

Examine the changes introduced by a commit:
```
/review:commit a1b2c3d
```

## Disclaimer

Not affiliated with OpenAI or Google. Just a set of custom commands using public prompt techniques.
