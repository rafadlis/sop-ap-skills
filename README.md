# SOP AP skills

Reusable skills for drafting and reviewing Indonesian government SOP AP under Permen PANRB Nomor 35 Tahun 2012. Each skill includes the original regulation and annex, source page citations, and optional SOP Studio guidance.

| Skill | Use |
| --- | --- |
| `sop-ap-author` | Draft or revise the identity sheet, actor lanes, branching flowchart and mutu baku |
| `sop-ap-review` | Review an SOP with evidence, source citations and specific corrections |

The skills work with supplied documents, files or process notes. A SOP Studio connection is needed only when you request reads or edits in that application.

## Install across projects

Use the [Skills CLI](https://skills.sh/docs/cli) to install both skills globally and select your agent applications:

```sh
bunx skills add rafadlis/sop-ap-skills --global --skill sop-ap-author sop-ap-review
```

Select specific agents when needed:

```sh
bunx skills add rafadlis/sop-ap-skills --global --skill sop-ap-author sop-ap-review --agent codex claude-code cursor
```

If Bun is unavailable, replace `bunx` with `npx`. Omit `--global` to install in the current project. The CLI controls the supported agents and installation locations; consult its current help for other applications.

List the package without installing:

```sh
bunx skills add rafadlis/sop-ap-skills --list
```

## Use

In an agent that supports named skill invocation:

```text
Use $sop-ap-author to draft this SOP in Bahasa Indonesia under Permen PANRB 35/2012. List facts that need confirmation.
```

```text
Use $sop-ap-review to review this SOP against Permen PANRB 35/2012. Cite the rule pages and report gaps without changing the document.
```

Other agents may expose skills through their own picker or command syntax. The `SKILL.md` instructions and relative reference files remain portable.

## Codex and manual installation

You can ask Codex's skill installer to install the published folders:

```text
Use $skill-installer to install both skills from https://github.com/rafadlis/sop-ap-skills, paths skills/sop-ap-author and skills/sop-ap-review.
```

For manual installation, download the [latest release](https://github.com/rafadlis/sop-ap-skills/releases/latest) and copy each complete folder under `skills/` into your agent's user-level skill directory. Keep `references/`, `agents/` and the license with each `SKILL.md`. Current Codex documentation describes `~/.agents/skills` as a user-level location; older installations may also use `~/.codex/skills`. Follow your installed client's documentation.

The repository also contains a portable, skills-only `plugin.json` manifest for compatible plugin hosts. Publication here does not imply a listing or approval in a public plugin marketplace. See the [official OpenAI packaging guide](https://developers.openai.com/plugins/build/plugins) for supported import paths.

## Source and verification

The bundled PDF is the 63-page official [JDIH BPK copy of Permen PANRB 35/2012](https://peraturan.bpk.go.id/Home/Download/123614/PERMENPAN%20NOMOR%2035%20TAHUN%202012.pdf), retrieved on 2026-10-09. Its SHA-256 is `665a31b3b3773d5a76f703d18c6d7ecad552bc783143db60e93f54bcbdb2baa9`. The [official record](https://peraturan.bpk.go.id/Details/132829/permen-pan-rb-no-35-tahun-2012) gives its legal metadata and status.

Initial validation checked skill frontmatter, local references, UI metadata, PDF hashes and sample drafting/review behavior. A draft or software lint pass does not establish formal institutional approval. The skills preserve unresolved facts and distinguish app behavior from the regulation.

## License

Original skill instructions and repository documentation are available under the MIT license. The bundled regulation is an unmodified official third-party source and is excluded from the MIT license grant. See [NOTICE](NOTICE).
