# stc CLI contract

## Discovery and recommendation

```bash
stc scan <path> --remote 20 --json --no-interactive
stc find <query> --json --no-interactive
```

`scan --remote` sends only public tokens derived from stc's built-in signal dictionary. It rebuilds signals from current project state on every run. Read `remote.recommendations[].entry` for `source`, `skill`, `name`, `installs`, and stable provider identity. Read `role` (`framework`, `component`, or `engineering`), `primarySignal`, and `scenario` as baseline explanations, not as installation authority.

`remote.page` describes the returned JSON batch. Interactive scans retain a larger finite candidate pool and allow unlimited `Next batch` / `换一批` actions, wrapping to the first batch after every unique candidate has been shown. JSON intentionally omits the hidden candidate pool; use targeted `find` queries when semantic analysis needs broader framework or component coverage.

`find --json` requires a query. Search every detected core framework and actual component, plus important tasks that need better coverage. Never send absolute paths, repository names, private package names, source code, or document text.

## Read-only inspection

```bash
stc inspect <source> --skill <name> --json
```

Inspection downloads through stc's internal Source Provider, returns normalized metadata and `SKILL.md` content, then removes temporary artifacts. It does not write registry or Agent directories.
Content larger than 256 KiB is rejected rather than truncated, so an agent never evaluates an incomplete Skill silently.

## Installation planning and execution

```bash
stc add <source> --skill <name> --dry-run --json
stc add <source> --skill <name> -y --json
```

The dry-run result contains `operations` with `install`, `skip`, or `replace` actions and their registry destinations. A same-name existing entry is skipped unless `--force` is explicitly planned. `--force` changes provenance and replaces the managed registry snapshot.

Use only exact source + Skill pairs returned by stc. Before executing an approved plan, repeat dry-run when the plan is old or upstream state may have changed. Stop when source identity, conflicts, or actions differ.

## Project state

```bash
stc project init
stc project add --from-bookmark <bookmark>
stc plan --json
stc apply --dry-run
stc apply -y
stc check --frozen
```

Registry installation does not imply project activation. Obtain separate approval before creating or merging `stc.yaml`, injecting directories, or applying a project plan.

## Bundled Agent Skill

```bash
stc agent install --agent <codex|agents|claude|cursor> --dry-run --json
stc agent install --agent <codex|agents|claude|cursor> -y --json
```

This explicit command is the only stc flow allowed to write a global Agent Skill directory. Existing destinations require `--force`; dry-run never writes.

## Exit behavior

- `0`: completed, including valid no-op or dry-run.
- `1`: source, network, validation, filesystem, or execution failure.
- `2`: invalid CLI input or a required non-interactive confirmation is missing.

Machine callers must parse JSON fields rather than human-readable text. Human output is bilingual and may evolve.
