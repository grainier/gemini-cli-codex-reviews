# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

This repository provides custom slash commands for Gemini CLI and Claude Code that bring OpenAI Codex-style code review prompts. It contains TOML files (for Gemini) and Markdown files (for Claude) that define `/review` commands with structured output (P0-P3 priority ratings).

## Repository Structure

- `gemini/review.toml` - Gemini: reviews current uncommitted changes
- `gemini/review/branch.toml` - Gemini: reviews changes against a base branch
- `gemini/review/commit.toml` - Gemini: reviews a specific commit SHA
- `claude/review.md` - Claude: reviews current uncommitted changes
- `claude/review/branch.md` - Claude: reviews changes against a base branch
- `claude/review/commit.md` - Claude: reviews a specific commit SHA

## Installation Target

Gemini CLI files are copied to `~/.gemini/commands/`:
- `gemini/review.toml` → `~/.gemini/commands/review.toml`
- `gemini/review/*.toml` → `~/.gemini/commands/review/`

Claude Code files are copied to `~/.claude/commands/`:
- `claude/review.md` → `~/.claude/commands/review.md`
- `claude/review/*.md` → `~/.claude/commands/review/`

## Command Format

### Gemini CLI (TOML)
- `description` - Short description shown in command help
- `prompt` - Prompt template with:
  - `{{args}}` - User-provided arguments
  - `!{command}` - Shell command interpolation (e.g., `!{git diff ...}`)

### Claude Code (Markdown)
- Plain markdown files with the prompt as content
- `$ARGUMENTS` - User-provided arguments
- No shell interpolation; prompts instruct Claude to run git commands directly
