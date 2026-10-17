# Research and evidence notes

**Reviewed:** 2026-10-07 (local system time, WAT)  
**Scope:** the GitHub and LinkedIn URLs supplied by the user; the live portfolio URL; the GitHub public-repository listing; and selected files/history under `/Users/cc/Repo`.

## Findings from public profiles

- GitHub identifies the account as `chideracollins`, with display name **Collins Chidera Eze**, location **Nigeria**, and a bio focused on applied LLMs and generative AI. GitHub returned 42 public repositories at review time.[2][3]
- LinkedIn displays **Collins Eze**, reports location as **Enugu State, Nigeria**, and lists four roles: CEO at VIVIDLY (Sep 2025–present), CEO at Speech (Jul–Oct 2025), Data Scientist at Decent Jobs Tech Skills Ltd (Jan 2024–Aug 2025), and CEO at rapidClient (Oct 2023–Aug 2025). It lists a B.Eng. in Electronic and Computer Engineering from the University of Nigeria, Nsukka (2019–2024).[1]
- These LinkedIn items are self-reported profile content; this research did not independently verify employment, degree completion, titles, dates, or outcomes. The resume preserves the listed titles/dates without adding responsibilities or metrics.

## Technical evidence reviewed

### Strongest public project proof

- `flutter_ui_migration_lint`: local repository `/Users/cc/Repo/flutter_ui_migration_lint`; clean working tree; first commit authored as `chideracollins` on 2026-09-08. Read the README, `pubspec.yaml`, implementation, and test file. The implementation detects configured Flutter imports, emits diagnostics, supports exclusion globs/URI overrides, and provides an import-rewrite fix. The test file covers diagnostics, already-migrated imports, the quick-fix, and exclusions. Tests were **not run** during this resume research. The public repository URL is listed on the GitHub profile.[3][4]

### Additional project evidence

- `my_quest`: local repository `/Users/cc/Repo/my_quest`; committed history is authored as `chideracollins` through 2026-10-06 and the working tree was clean when checked. Read the project guide, product brief, package manifest, journal repository implementation, and AI-question provider. Evidence shows an in-progress Flutter/Dart journaling app using Isar for journal records and Riverpod for an AI-question stream that selects local or cloud model providers. Its repo is local/private in the reviewed material; no public source link or user metrics were found. Runtime behavior and tests were not exercised.
- `chideracollins.github.io`: local repository `/Users/cc/Repo/chideracollins`; first iteration authored as `chideracollins` on 2026-10-07. Read the README, package manifest, and React components. The live site is accessible and the code persists the theme selection in `localStorage`.[6][7] The page currently markets the candidate as open to **senior** mobile/backend/AI-agent roles and claims FastAPI, MCP, autonomous-agent, architecture, and production-grade expertise.[7] The reviewed project evidence does not substantiate all of those claims; this is a **not-yet-assessed gap**, not proof the skills are absent. To protect credibility, either add concrete, reviewable project evidence (tests, deployment, contribution, design decisions) for these claims or narrow the portfolio language. The resume omits the live portfolio link until this mismatch is resolved.
- `speech-cli`: the public README describes a Python natural-language software-building CLI and the GitHub page shows four contributions by `chideracollins`; this review did not inspect its source code or validate the feature claims, so it is **not included** in the resume yet.[5]
- `storrs-business`: local shared repository at `/Users/cc/Repo/storrs-business`, with commits authored as `chideracollins` in April 2026. The README describes a Flutter merchant app; the commit log includes work on AI-ads management, sales-module restructuring, shared UI, and documentation. The working tree contained many uncommitted changes. Those diffs were deliberately not opened; no client/employment relationship or permission to identify the project on a resume was confirmed. It is kept out of the resume pending confirmation.
- `JustHireMe`: local repository is a fork; its README names Vasudev Siddh as maintainer, and the sampled recent commit history belongs to that maintainer. The local working tree also had an uncommitted package-lock change. It is **not represented as the candidate's project**.

## Local repository scan

The requested `~/Repo` folder contained seven Git repositories: `chideracollins`, `flutter_ui_migration_lint`, `js-tutorials`, `js-web-games`, `JustHireMe`, `my_quest`, and `storrs-business`. Review was selective: project READMEs/manifests and a small number of relevant source/test files were read; no secrets, `.env` files, credential/config values, or uncommitted diffs were inspected. Repository inventory for all 42 public GitHub repositories is in `repository_inventory.json`.[3]

## Resume gaps and next steps

1. **Choose a target role and level.** “Software developer / applied AI” is an initial positioning inferred from the profile and projects, not a confirmed job target.
2. **Confirm identity/contact:** preferred resume name (GitHub and LinkedIn use different forms), current city/country, email, phone (if desired), and work authorization only if relevant.
3. **Validate profile-listed work and education:** confirm the four job titles/dates, exact organization names, whether VIVIDLY's title should include co-founder, and whether the degree was awarded.
4. **Add role evidence:** for each position, supply actual scope, technologies, decisions, collaboration, and outcomes. No revenue, user counts, model quality, latency, or business impact figures were found or invented.
5. **Resolve public portfolio claims:** substantiate or narrow the current senior/FastAPI/MCP/AI-agent claims before using that URL in applications.[7]
6. **Decide whether to publish private/shared project work:** confirm the My Quest demo/link and whether the Storrs contribution can be named publicly; do not expose proprietary details without approval.
7. **Verify behavior:** run the relevant project tests/builds before describing those projects as tested or production-ready.

## Sources

[1] https://linkedin.com/in/cceze — LinkedIn profile — Collins Eze
[2] https://github.com/chideracollins — GitHub profile — chideracollins
[3] https://api.github.com/users/chideracollins/repos?per_page=100&sort=updated — GitHub public repository listing
[4] https://github.com/chideracollins/flutter-ui-migration-lint — flutter_ui_migration_lint repository
[5] https://github.com/chideracollins/speech-cli — speech-cli repository
[6] https://github.com/chideracollins/chideracollins.github.io — Portfolio repository
[7] https://chideracollins.github.io — Live portfolio website
