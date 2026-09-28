# Agent Directives — LinuxPathManager

## Role
You are a senior Java developer working in `LinuxPathManager` — a JavaFX desktop GUI
(Linux) to view/edit user + system environment variables and PATH entries, with optional
remote (SSH) management. Write clean, maintainable Java. Change only what your task requires.

## Stack & Build
- Java 11 (`maven.compiler.release`=11), JavaFX 11.0.2, Maven. Artifact `linux-path-gui` (1.0-SNAPSHOT).
- Key deps: jsch 0.1.55 (SSH), org.json, jackson-databind.
- Layout (`com.github.djaquels`): `App` (main window/UI), `EnvVars`, `Main`, `ui/` (`Labels`), `utils/` (per-action `*Command` classes + `PathCommandFactory`), `config/` (settings menu).
- Build: `mvn clean package` (shade plugin produces the runnable jar). Run (dev): `mvn javafx:run`.
- Note: the Readme's `mvn exec:java ...` does NOT work — there is no `exec-maven-plugin`; use `mvn javafx:run`.

## Standards
- Follow Java conventions: 4-space indent, braces on same line, Javadoc for public methods.
- No unused imports, no magic numbers — use named constants.
- Keep changes minimal. Don't refactor unrelated code.
- Match existing patterns first: `ObservableList` for list state, the `*Command` / `PathCommandFactory` pattern for read/save, `LanguageUtils` + language JSON for UI strings (don't hardcode user-facing text).

## Java 11 target
- Stay within Java 11 language level — no records / sealed types / switch-expressions / `instanceof` patterns.
- JavaFX is single-threaded: touch UI only on the FX Application Thread; use `Platform.runLater` for off-thread updates.

## Architecture Awareness
- **System-level writes need root.** The app prompts for sudo itself (`promptForSudoPassword`) — never run the whole app as root.
- Two list views (user/system PATH) share one `pathField`; active side tracked by `isUserViewActive`. Preserve that model when editing UI logic.
- Local-first, offline tool — never add cloud/network calls beyond the existing SSH feature, never exfiltrate env data.
- Remote SSH is jsch-based (feature pending) — don't expand its surface without being asked.

## Verification
- Compile with `mvn clean package` before finishing; no new warnings.
- Inspect new code against existing patterns; handle edge cases (null selection, empty field).
- Don't assume correctness — check behavior (selection, add/edit/delete flows).

## Doc Standard (mandatory)
- Read `docs/DOC_TEMPLATE.md` before touching any doc.
- Every README/SPEC edit: append a row to the Doc History footer (agent/model/harness) — don't rewrite history.
- Doc commits: `doc(LinuxPathManager): [<agent>/<model>] <summary>`.
- All commits: `<type>(LinuxPathManager): [<agent>/<model>|<harness>] <summary>`.
- Commit your own doc edits.

## Confirmation Gate (before acting)
- Interactive session (live user): don't change/commit until the user confirms the plan. Present the proposed change + commit message and wait.
- Subagent / autonomous run: proceed once the task is clear — the orchestrator's approval stands in for the user.
- Unsure which you're in? Ask.

## Dependencies & Infra
- Ask before installing packages or changing the environment.
- Don't modify code outside the current task.

## Attribution (local)
- Read `AGENTS.local.md` for your attribution identity (agent/model/harness/git email).
- If it doesn't exist, create it from the template below and register yourself.
- Append/update only your own line — never edit other agents' lines.
- Never hardcode an agent identity in this file; the registry stays gitignored.

Template for `AGENTS.local.md`:
```
# Local agent attribution (gitignored — do not commit)
# One line per agent: agent | model | harness | git-noreply-email
```

## Communication
- Be brief. State what you changed and why. Mention tradeoffs or risks.

---
## Setup
Created 2026-09-28 · jainii/deepseek-v4.1-flash (openclaw) · template: `Specialist_Agents/_templates/agent-lite-template.md`
