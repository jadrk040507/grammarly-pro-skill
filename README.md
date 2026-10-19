# Grammarly Pro skill for Codex

An unofficial, instruction-only skill for using Grammarly Pro through your existing signed-in browser. It supports proofreading, AI and plagiarism checks, Humanizer, paraphrasing, and natural-voice editing while preserving facts and citations.

This is not a Grammarly MCP server, browser extension, or official Grammarly/OpenAI integration. Installing the skill adds workflow instructions; it does not install or grant browser access.

## Requirements

- Codex or another compatible Agent Skills host.
- A browser-control integration available to the agent, with its documented UI/accessibility or DOM controls. The workflow was exercised with Codex's connected Chrome browser. A terminal-only Codex session without browser tools cannot perform Grammarly checks.
- Your own signed-in Grammarly account with access to the requested Pro features. Agent availability and UI can vary by account and product version.
- Git for the installation commands below.

No Grammarly API credentials, password export, or separate cloud browser account is required. The skill itself has no executable scripts or dependencies.

## Install for one project

Run these commands from your project's root:

```bash
mkdir -p .agents/skills
git clone --depth 1 https://github.com/jadrk040507/grammarly-pro-skill.git .agents/skills/grammarly-pro
```

The skill is discovered for that project. The destination must not already exist. This makes a nested Git checkout; if you want your team to track the files in the parent repository, copy `SKILL.md`, `agents/`, and `references/` into its `.agents/skills/grammarly-pro/` folder from a separate clone instead.

## Install globally for your user

```bash
mkdir -p "$HOME/.agents/skills"
git clone --depth 1 https://github.com/jadrk040507/grammarly-pro-skill.git "$HOME/.agents/skills/grammarly-pro"
```

This makes it available across your projects. Choose one scope per installation. If you already installed a copy under `~/.codex/skills/grammarly-pro`, keep using that copy or move it to the current user skill location; do not add a duplicate with the same skill name. For installations with a custom skill root, use the directory configured by your host.

Codex detects skill changes automatically; restart it if the skill does not appear. See the [official skill locations and discovery documentation](https://learn.chatgpt.com/docs/build-skills#where-codex-loads-local-skills).

## Use

```text
Use $grammarly-pro to proofread this draft, check AI and plagiarism results,
and make it sound natural while preserving every fact and citation.
```

You can also request individual operations:

- “Use Grammarly to check this paragraph's grammar and clarity.”
- “Run AI and plagiarism checks and report only the displayed results.”
- “Use Grammarly's Humanizer on a copy of my paper in an academic voice.”
- “Make this sound more natural here in Codex without submitting it to Grammarly.”

The skill keeps the original, verifies that the whole intended text reached the editor, distinguishes original and revised scores, and reviews proposed rewrites before applying them. Natural-voice edits do not guarantee a particular detector score.

## Update or uninstall

For a Git-based project install:

```bash
git -C .agents/skills/grammarly-pro pull --ff-only
```

For a Git-based global install:

```bash
git -C "$HOME/.agents/skills/grammarly-pro" pull --ff-only
```

If you edited the installed files, preserve your edits before updating. To uninstall, remove only the `grammarly-pro` skill directory at the scope you selected. This does not delete Grammarly documents or alter your account.

## Data handling and limits

Grammarly checks submit the chosen text to Grammarly through its web UI. Codex-based editing uses your Codex session and its model service. The skill does not add third-party browser hosting, export session cookies, call private Grammarly APIs, or configure additional model providers. Your existing browser integration still has its own permissions and data-handling terms.

Proofreading, completed AI detection, completed plagiarism checking, and native Humanizer preview generation were tested with a synthetic paragraph. Accepting the generated rewrite was not verified. AI Rewriter and Paraphraser controls were observed, but their execution was not tested. Browser UI changes, processing failures, quotas, and account feature availability can affect operation. Missing or unfinished results must be reported as unavailable, not guessed.

This project is not affiliated with or endorsed by Grammarly, Superhuman, or OpenAI. Their names and marks belong to their respective owners.

## License

[MIT](LICENSE).
