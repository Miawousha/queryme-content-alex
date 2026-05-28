# queryme-content-alex

Persona content for the [queryme](https://github.com/alexcollet/queryme) deployment.

This repo holds the system prompt, the public knowledge base, the CV
curation, and the persona identity (name, pronouns). The queryme app
pulls from this repo via its admin Content tab.

## Layout

- `persona.yaml` — identity (name, pronouns)
- `prompts/system.md` — system prompt
- `cv-config.yaml` — curation for the printable CV
- `kb/` — knowledge base (profile, skills, education, experience, projects, etc.)

## Editing

Edit any file, push to `main`, then click **Sync** in the queryme admin panel.
