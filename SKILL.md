---
name: organize-project-knowledge
description: Audit and reorganize messy project documentation into a reliable operating system with explicit sources of truth, current state, append-only history, roadmap, technical debt, test ownership, pending human checklists, acceptance records, archives, backups, and storage boundaries. Use for project-wide documentation cleanup, duplicate or conflicting files, unclear “what was done vs what remains,” private-workspace versus Git/public-repository governance, test and acceptance redesign, or requests such as “整理项目文档”, “项目记忆”, “以前测了什么”, and “以后要测什么”.
---

# Organize Project Knowledge

Treat project documentation as an operating system for decisions and execution, not as a pile of files. Preserve evidence, make every information class have one authority, and prove the result with measurable checks.

## Apply the Operating Principles

- Audit the whole project before declaring a local problem solved. A clean set of six files does not prove that the rest of the project is clean.
- Give every information class one source of truth. Let other files link to it instead of restating it.
- Separate current truth, historical truth, future intent, unresolved debt, reusable procedure, pending work, and completed evidence.
- Distinguish exact duplicates, semantic overlap, obsolete entry points, deliberate mirrors, and dated snapshots. Do not call files duplicates merely because their names resemble each other.
- Make storage boundaries explicit. A private workspace and a code repository may have different structures and content.
- Preserve recoverability before bulk moves, rewrites, archive compression, or deletion.
- Report completion with counts, paths, hashes, link checks, and scoped diffs rather than saying that the result “looks cleaner.”

## Choose the Work Mode

Match actions to the user's request:

- For an audit, explanation, or plan, inspect and report without mutating files.
- For an implementation request, make a recoverable backup, reorganize the files, update links, validate the result, and summarize evidence.
- For an ambiguous destructive step, finish all safe analysis first and request confirmation only for the destructive boundary.

Preserve unrelated user changes and dirty repositories throughout either mode.

## Run the Workflow

### 1. Discover Every Documentation Surface

Locate all relevant roots before analyzing individual documents:

- private project folders, NAS or shared-workspace copies;
- code-repository documentation;
- generated mirrors and synchronization targets;
- current navigation pages and indexes;
- archive folders, backups, and unpacked snapshots;
- test plans, human checklists, reports, and acceptance evidence.

Inventory paths, sizes, timestamps when useful, and SHA-256 hashes. Read navigation documents and representative content; filenames and hashes alone cannot reveal semantic overlap or contradictory authority.

Classify each item as current state, history, roadmap, technical debt, procedure, pending AI/platform testing, pending human testing, completed acceptance evidence, archive, template, generated mirror, or sensitive/private material.

### 2. Define Authority Before Moving Files

Create a small authority matrix tailored to the project. Use this model unless the existing project requires another explicit design:

| Information class | Required behavior |
| --- | --- |
| Current state / project memory | Keep one concise, replaceable source of present truth. |
| Project history memory | Keep one append-only chronological record of meaningful decisions and completed changes. |
| Roadmap | Hold future work that is intended but not currently done. |
| Technical debt | Hold known problems and deferred remediation, not ordinary roadmap work. |
| Procedures | Explain how to perform a repeatable action; never imply that it was performed. |
| Pending AI/platform tests | Track checks executable by automation, an agent, CI, or the platform. |
| Pending human tests | Use a checkbox-oriented black-box acceptance file for work only a person can judge. |
| Acceptance records | Preserve dated results from AI, platform, and human testing, including environment and evidence. |
| Archives | Preserve old evidence without acting as a current entry point. |

Do not force the private workspace and Git repository to mirror one another. Instead, state:

1. which system is authoritative for each information class;
2. which documents are allowed to sync;
3. which documents must remain private;
4. which direction synchronization flows;
5. how generated copies are recognized so they are not edited as authorities.

Allow credentials only in an explicitly authorized private secret location. Never copy passwords, tokens, API keys, private endpoints, or unmasked secret values into Git, GitHub, CI logs, public documentation, shareable reports, or chat output.

### 3. Design the Target Information Lifecycle

Use directories and filenames that express state, not multiple competing entry points. Keep the exact names compatible with the project's language and conventions.

Apply these lifecycle rules:

- Replace the current-state document when reality changes; do not append a diary to it.
- Append decisions and completed milestones to project history; do not rewrite prior history silently.
- Put unstarted intended work in the roadmap and discovered deferred problems in technical debt.
- Keep human black-box criteria in a pending checklist that is easy to tick.
- After executing a pending test file, add date, version, environment, actor, outcome, exceptions, and evidence, then move that same file into acceptance records. Do not create a second near-duplicate record.
- Keep reusable templates blank and clearly labeled as templates.
- Make summary reports link to evidence instead of copying the evidence.
- Keep superseded material in dated archives, detached from current navigation.

Create one short entry page when navigation is confusing. It should answer only:

1. What has already been done?
2. What needs to be done now?
3. How should it be tested?
4. What standard counts as accepted?

### 4. Back Up Before Material Reorganization

Before bulk reorganization:

1. Generate a manifest containing relative path, size, and SHA-256 for the documentation root.
2. Copy the complete documentation root to an independent destination; prefer an external drive or another physically independent store when available.
3. Generate or verify the destination manifest.
4. Compare source and backup and record the result.
5. Perform no deletion in the backup stage.

Keep raw originals in a dated archive when normalizing content. Compress large expanded snapshots only after saving a manifest and hash and proving that extraction restores the expected files.

### 5. Reorganize Without Multiplying Truth

- Move an authority instead of copying it when the same content would otherwise remain current in two places.
- Merge genuinely overlapping content into the selected authority, then archive the replaced entry point.
- Mark obsolete plans or checklists as superseded when historical context still matters.
- Update indexes, cross-links, synchronization rules, and scripts that could regenerate retired paths.
- Search both filenames and file contents for old paths after moves.
- Keep code-bound documentation near the code when that improves maintenance; keep operational memory, private records, and sensitive material in the private workspace.

### 6. Validate the New System

Run checks proportional to the change and record the findings:

- source and backup file counts and manifest equality;
- exact duplicate groups by SHA-256;
- semantic-overlap groups resolved or explicitly justified;
- broken internal links and missing targets;
- stale path references in content and sync scripts;
- number of current-state authorities for each information class;
- number of active pending human checklists for the same acceptance target;
- clear separation of procedures, pending work, and completed evidence;
- public-repository secret scan with zero exposed credentials;
- Git status and diff limited to the intended scope.

Do not claim that a feature passed merely because a procedure exists or a checklist is present. Acceptance requires a dated result and attributable evidence.

## Maintain by Events, Not Calendar Ritual

During active development, update the system when meaningful events occur:

- after completing a material change, update current state and append project history;
- when adding intended future work, update the roadmap;
- when discovering a deferred problem, update technical debt;
- when a test becomes executable, place it in the appropriate pending area;
- after testing, move the completed file into acceptance records with evidence;
- before risky reorganization or release, create and verify a backup;
- when launching or entering a genuinely new lifecycle, design the next lifecycle explicitly.

Do not split records by month merely to satisfy a schedule unless the project's volume or compliance needs justify it.

## Deliver the Result

Summarize the outcome in this order:

1. what the project now treats as authoritative;
2. what was moved, merged, archived, or deliberately left separate;
3. what remains pending and who or what owns each test;
4. how backup, links, duplicates, secrets, and repository scope were verified;
5. which event-driven rules maintain the system going forward.

Mention unresolved ambiguity explicitly. Never hide uncertainty by creating another document that competes with the existing authorities.
