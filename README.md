# Ernie Francis IV Portfolio

This repository hosts the personal website and portfolio of Ernie Francis IV, IT Lead at Cornell Cooperative Extension and web developer.

## Agent Setup

To ensure a consistent experience for AI agents (such as Hermes, Claude Code, and GitHub Copilot) when working on this repository, we have installed a set of agent skills from the [skills.sh](https://skills.sh) registry.

### Installed Skills

The following skills have been installed for this repository:

1. **web-design-guidelines** (from `vercel-labs/agent-skills`)
   - Provides guidelines for web design and best practices.
2. **frontend-design** (from `anthropics/skills`)
   - Focuses on frontend development principles and patterns.
3. **verification-before-completion** (from `obra/superpowers`)
   - Encourages verifying work before marking tasks as complete.

### Installation Details

- **Scope**: The skills are installed in a project-scoped manner under `.claude/skills/` (copied, not symlinked). This ensures that the skill versions are pinned to the repository and reviewable in pull requests (vendoring approach).
- **Agents**: The skills are installed for the `claude-code` agent and also made available to all agents (via the `*` agent selector) to maximize compatibility.
- **Hermes Compatibility**: Note that Hermes Agent uses its own skill system, located at `$HERMES_HOME/skills/` (by default `~/.hermes/skills/`). The skills installed via `npx skills` are not automatically available to Hermes. To use the same skills with Hermes, you can install them via the Hermes CLI:
  ```bash
  hermes skills install vercel-labs/agent-skills/web-design-guidelines
  hermes skills install anthropics/skills/frontend-design
   hermes skills install obra/superpowers/verification-before-completion
  ```
  For project isolation with Hermes, consider using a dedicated profile or setting the `HERMES_HOME` environment variable to a local directory when working on this repo.

### Verification

Before installing, we reviewed the source repositories for each skill on [https://www.skills.sh/audits](https://www.skills.sh/audits) to ensure they meet safety and quality standards.

### Commands Used

The following commands were used to set up the agent skills (executed from the repository root):

```bash
# Install web-design-guidelines for claude-code (copied)
npx skills add vercel-labs/agent-skills --skill web-design-guidelines --agent claude-code --copy --yes

# Install frontend-design for claude-code (copied)
npx skills add anthropics/skills --skill frontend-design --agent claude-code --copy --yes

# Install verification-before-completion for claude-code (copied)
npx skills add obra/superpowers --skill verification-before-completion --agent claude-code --copy --yes

# Install all three skills for all agents (copied)
npx skills add vercel-labs/agent-skills --skill web-design-guidelines --agent '*' --copy --yes
npx skills add anthropics/skills --skill frontend-design --agent '*' --copy --yes
npx skills add obra/superpowers --skill verification-before-completion --agent '*' --copy --yes
```

### Notes

- The skills are stored in `.claude/skills/` and are committed to this repository.
- The `skills-lock.json` file records the exact versions of the installed skills for reproducibility.
- No changes were made to `index.html`, `script.js`, or `style.css` as part of this setup.