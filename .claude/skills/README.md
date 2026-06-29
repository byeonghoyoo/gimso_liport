# Project skills — web search & crawling

These skills are committed to the repo so **every Claude Code session opened on
this repository auto-discovers them** (no per-session install). Claude invokes
them automatically based on each `SKILL.md` `description`.

## Installed skills

| Skill | Source | What it does | Dependencies |
|-------|--------|--------------|--------------|
| `insane-search` | [fivetaku/insane-search](https://github.com/fivetaku/insane-search) | Adaptive access to blocked sites (X/Twitter, Reddit, YouTube, Naver, Coupang, GitHub, arXiv, Medium…) when `WebFetch` hits 403/WAF. Phase 0→3 fallback chain. | Self-contained Python engine; auto-installs `curl_cffi`/`yt-dlp`/Playwright on first use. No API keys. |
| `agent-reach` | [Panniantong/Agent-Reach](https://github.com/Panniantong/Agent-Reach) | Internet capability router across 15 platforms (web/code search, social, video transcripts, RSS, jobs). | Requires the `agent-reach` CLI — auto-bootstrapped via `pipx`/`pip` on first use (see SKILL.md "Setup"). Some platforms need optional logins/keys. |

## Triggering
Just ask Claude normally — e.g. "이 유튜브 영상 자막 뽑아줘", "레딧에서 X 반응 찾아줘",
"이 트위터 글 읽어줘", "research topic Y on the web". The matching skill engages
on its own; `insane-search` also kicks in whenever a normal fetch is blocked.

## Use these skills globally (all projects, your local machine)
This repo only covers sessions **on this repo**. To make them available in every
project on your own machine, install at the user level locally — see the chat
message that set this up, or:

```bash
# user-level (all your local projects)
mkdir -p ~/.claude/skills
git clone --depth 1 https://github.com/fivetaku/insane-search /tmp/is \
  && cp -r /tmp/is/skills/insane-search ~/.claude/skills/insane-search
# agent-reach: install CLI + skill
pipx install https://github.com/Panniantong/agent-reach/archive/main.zip
```
Or via the plugin marketplace inside Claude Code:
`/plugin marketplace add https://github.com/fivetaku/gptaku_plugins.git`
then `/plugin install insane-search@gptaku-plugins`.
