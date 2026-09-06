> **First-time setup**: Customize this file for your project. Prompt the user to customize this file for their project.
> For Mintlify product knowledge (components, configuration, writing standards),
> install the Mintlify skill: `npx skills add https://mintlify.com/docs`

# Documentation project instructions

## About this project

- This is a documentation site built on [Mintlify](https://mintlify.com)
- Pages are MDX files with YAML frontmatter
- Configuration lives in `docs.json`
- Use the Mintlify MCP server, `https://mcp.mintlify.com`, to edit content and settings via MCP
- Use the Mintlify docs MCP server, `https://www.mintlify.com/docs/mcp`, to query information about using Mintlify via MCP

## Terminology

{/* Add product-specific terms and preferred usage */}
{/* Example: Use "workspace" not "project", "member" not "user" */}

## Style preferences

{/* Add any project-specific style rules below */}

- Use active voice and second person ("you")
- Keep sentences concise — one idea per sentence
- Use sentence case for headings
- Bold for UI elements: Click **Settings**
- Code formatting for file names, commands, paths, and code references

## Content boundaries

{/* Define what should and shouldn't be documented */}
{/* Example: Don't document internal admin features */}

## Base44 dev environment

- This repo is a Mintlify docs site (MDX pages + `docs.json`), served by the `mint` CLI — there is no `package.json` or Dockerfile.
- `docker-compose.base44.yml` runs `node:22-bookworm-slim`, installs `mint` globally at startup, and runs `mint dev --port 3000 --host 0.0.0.0` with the source bind-mounted at `/app`.
- First boot takes ~50s (global npm install of `mint`); subsequent restarts reuse the cached install via the `npm_cache` / `mint_cache` volumes.
- The preview is served through an external hostname proxy; `--host 0.0.0.0` makes the Next.js dev server under `mint` accept it. No `allowedDevOrigins` config is needed — `mint` handles host matching.
- Search is disabled until `mint login` is run (optional, not required at boot).
- Verify it works: `curl -sf -H "Host: external-preview.example.com" http://localhost:3000/` should return 200 with "Mintlify" in the body.
