# **Contributing Guidelines - HipoSim Report**

This document defines the collaboration rules, Git workflow, contribution standards, and responsibilities for the `hiposim-report` repository developed by the **AuraCode** team for the **HipoSim** project.

## **Project Information**

- **University:** Universidad Peruana de Ciencias Aplicadas (UPC)
- **Program:** Software Engineering
- **Course:** 1ASI0732 - Diseño de Experimentos de Ingeniería de Software
- **NRC:** 9104
- **Academic Period:** 202620
- **Team:** AuraCode
- **Project:** HipoSim
- **Repository:** `hiposim-report`

## **Team Members**

The team is composed of **5 members**:

- Bautista Rivera, Jose Diego - U202310949
- Carlos Lavado, Ever Giusephi - U202224867
- Daga Chávez, Joaquín Leonardo - U202219829
- Janampa Gutierrez, Jhoan Darner - U202323319
- Lopez Roman, Franco Mauricio - U202315890
- Olivares Lao, Gustavo Alonso - U202216448

All team members must contribute to the report and provide verifiable evidence of participation through commits, branches, Pull Requests, reviews, and collaboration records.

## **Report Structure**

The report follows the structure defined for the Mobile Applications final project:

- Cover
- Report Version Log
- Project Report Collaboration Insights
- Content
- Student Outcome
- **Chapter I:** Introduction
- **Chapter II:** Requirements Elicitation & Analysis
- **Chapter III:** Requirements Specification
- **Chapter IV:** Product Design
- **Chapter V:** Product Implementation
- **Chapter VI:** Product Verification & Validation
- **Chapter VII:** DevOps Practices
- **Chapter VIII:** Experiment-Driven Development
- Conclusions
- Bibliography
- Annexes

Work is assigned according to the scope of each delivery and Sprint. Chapter ownership is **not permanent**: team members may act as leaders or collaborators depending on the aspect being developed.

For implementation-related work, the team must identify **Aspect Leaders and Collaborators** for the relevant Sprint and keep this distribution consistent with the evidence included in the report.

## **Responsibilities**

Every contributor must:

- Work only on tasks assigned or previously coordinated with the team.
- Keep the report structure consistent with the official course statement.
- Coordinate before editing shared files or sections.
- Keep the Table of Contents, Version Record, Student Outcome, and Collaboration Insights updated when applicable.
- Add or update the required evidence for the corresponding delivery.
- Validate links, images, tables, references, and Markdown formatting before requesting a merge.
- Keep commits small, clear, and related to one logical change.
- Participate in reviews of teammates' Pull Requests.
- Avoid modifying another member's active section without prior coordination.
- Ensure that contributions can be clearly traced to the author through Git history.

## **Delivery Milestones**

The project uses the following academic milestones:

- `av1` - Sprint Review
- `tb1` - Stage Review
- `av2` - Sprint Review
- `tb2` - Release Review

Every work branch related to the report must include the corresponding delivery identifier.

---

## **Branching Model - GitFlow**

The repository follows GitFlow.

### **Main branches**

- `main` - Stable and delivered versions only. **Do not work directly on this branch.**
- `develop` - Integration branch for work approved during the current delivery.

### **Supporting branches**

- `feature/<delivery>-<task-name>` - New report content, evidence, diagrams, or sections.
- `fix/<delivery>-<task-name>` - Corrections to existing report content.
- `release/<delivery>-v<major>.<minor>.<patch>` - Final preparation of an academic delivery.
- `hotfix/<task-name>` - Urgent corrections required after a release.
- `archive/<delivery>-<task-name>` - Optional archive for completed feature branches when the team wants to preserve branch evidence.

### **Branch Naming Convention**

Use lowercase English words separated by hyphens.

```text
feature/<av1|tb1|av2|tb2>-<task-name>
fix/<av1|tb1|av2|tb2>-<task-name>
release/<av1|tb1|av2|tb2>-v<major>.<minor>.<patch>
hotfix/<task-name>
```

### **Branch Examples**

```text
feature/av1-startup-profile
feature/av1-interview-analysis
feature/av1-target-segments
feature/tb1-user-stories
feature/tb1-sprint-backlog
feature/av2-validation-interviews
fix/tb1-table-of-contents
release/tb1-v0.2.0
hotfix/broken-report-links
```

> Use descriptive task names. Avoid personal names, initials, generic names such as `changes`, or branches that contain unrelated work.

---

## **Mandatory Workflow**

### 1. Update `develop`

Before starting new work:

```bash
git checkout develop
git pull origin develop
```

### 2. Create a work branch

Example:

```bash
git checkout -b feature/av1-interview-analysis
git push -u origin feature/av1-interview-analysis
```

### 3. Work on the assigned scope

While editing:

- Follow the existing repository structure.
- Use Markdown for report content.
- Store images and other report resources in the appropriate assets directory.
- Use relative paths whenever possible.
- Do not rename shared files without coordinating with the team.
- Do not combine unrelated report sections in the same branch.

### 4. Review local changes

Before committing:

```bash
git status
git diff
```

Check that:

- Only intended files were modified.
- No temporary files were added.
- Image paths and hyperlinks are valid.
- Markdown tables render correctly.
- Headings preserve the report hierarchy.

### 5. Commit using Conventional Commits

Example:

```bash
git add .
git commit -m "feat(chapter-2): add interview analysis"
```

### 6. Synchronize before pushing

If `develop` changed while you were working:

```bash
git fetch origin
git rebase origin/develop
```

If the team prefers merge-based synchronization for the current delivery, coordinate before doing so.

### 7. Push the branch

```bash
git push origin feature/av1-interview-analysis
```

If the branch was rebased after already being pushed:

```bash
git push --force-with-lease
```

Never use `--force` on shared branches.

### 8. Open a Pull Request

Every contribution must be merged through a Pull Request:

```text
feature/* -> develop
fix/*     -> develop
```

Pull Request requirements:

- Use a clear title.
- Explain what was added, changed, or corrected.
- Mention the related report section.
- Include screenshots when the change affects visual evidence or formatting.
- Request at least **1 review** from another team member.
- Resolve all conversations and conflicts before merging.
- Verify that the branch is up to date with `develop`.
- Do not approve your own Pull Request as the only review.

---

## **Pull Request Title Convention**

Use the same intent as Conventional Commits:

```text
feat(chapter-2): add candidate context discovery
docs: update collaboration insights
fix(chapter-3): correct mobile wireflow references
chore: reorganize report assets
```

## **Pull Request Description Template**

Recommended format:

```md
## Summary

Brief description of the contribution.

## Report Section

- Chapter / section:
- Delivery:

## Changes

- Change 1
- Change 2
- Change 3

## Validation

- [ ] Markdown renders correctly
- [ ] Images and links work
- [ ] Tables were reviewed
- [ ] Content matches the assigned scope
- [ ] No unrelated files were modified
```

---

## **Conventional Commits**

Commit messages must follow the Conventional Commits specification.

### Allowed types

- `feat:` - New report content or evidence.
- `docs:` - Documentation-only changes.
- `fix:` - Corrections to existing content.
- `refactor:` - Structural improvement without changing the intended content.
- `chore:` - Repository maintenance or asset organization.
- `style:` - Formatting changes that do not change the meaning.
- `test:` - Testing-related evidence or documentation, when applicable.

### Recommended scopes

Use scopes that identify the report area whenever useful:

- `assets`
- `cover`
- `logs`
- `insights`
- `content`
- `outcome`
- `chapter-1`
- `chapter-2`
- `chapter-3`
- `chapter-4`
- `chapter-5`
- `chapter-6`
- `chapter-7`
- `chapter-8`
- `conclusions`
- `bibliography`
- `annexes`

### Examples

```text
feat(chapter-1): add startup member profiles
feat(chapter-2): document bounded context canvases
feat(chapter-3): add mobile application mockups
feat(chapter-4): add sprint 1 development evidence
docs(outcome): update av1 actions
fix(content): correct chapter links
fix(bibliography): update apa references
chore(assets): reorganize interview screenshots
```

### Commit Rules

- Write commit messages in English.
- Use the imperative mood.
- Keep the subject concise.
- Do not use vague messages such as `update`, `changes`, `final`, `fix stuff`, or `avance`.
- Do not combine several unrelated tasks in one commit.

---

## **Release Process**

A release branch is created only when the content planned for the corresponding delivery has already been integrated into `develop`.

### 1. Update `develop`

```bash
git checkout develop
git pull origin develop
```

### 2. Create the release branch

Example for TB1:

```bash
git checkout -b release/tb1-v0.2.0
git push -u origin release/tb1-v0.2.0
```

### 3. Perform final validation

During the release, only make corrections necessary for delivery preparation.

Validate at minimum:

- Cover information.
- Version Record.
- Project Report Collaboration Insights.
- Table of Contents.
- Student Outcome.
- Required chapters for the current milestone.
- Conclusions.
- Bibliography and APA 7 formatting.
- Annexes.
- Image quality and paths.
- Internal and external links.
- Consistency of headings and numbering.
- PDF export.
- Evidence of contributions from all team members.

### 4. Merge the release

After approval:

```text
release/* -> main
release/* -> develop
```

Direct commits to `main` are not allowed.

### 5. Create a version tag

The repository uses Semantic Versioning.

Recommended academic milestone tags:

```text
AV1 -> v0.1.0
TB1 -> v0.2.0
AV2 -> v0.3.0
TB2 -> v1.0.0
```

Example:

```bash
git checkout main
git pull origin main
git tag -a v0.2.0 -m "TB1 release"
git push origin v0.2.0
```

Patch tags such as `v0.2.1` may be used when an approved delivery requires a subsequent correction.

---

## **Hotfix Process**

Use a hotfix only for an urgent correction to a version already integrated into `main`.

Example:

```bash
git checkout main
git pull origin main
git checkout -b hotfix/broken-report-links
```

After correction:

```text
hotfix/* -> main
hotfix/* -> develop
```

Create a new patch version tag when the correction modifies a released version.

---

## **Archiving Completed Branches**

After a delivery is completed, feature branches may be deleted after merge or preserved under `archive/` when the team needs explicit branch evidence.

Example:

```bash
git branch -m feature/av1-startup-profile archive/av1-startup-profile
git push origin archive/av1-startup-profile
git push origin --delete feature/av1-startup-profile
```

For the next delivery, always create new work branches from the updated `develop` branch.

---

## **File Organization**

Follow the structure already defined in the repository.

General rules:

- Main report content must use `.md` files.
- Keep the principal entry point as `README.md` when required by the report structure.
- Store visual resources in the repository's assets directories.
- Prefer clear, descriptive, lowercase file names.
- Avoid duplicated images and duplicated report content.
- Use relative paths for repository resources.
- Do not upload unrelated personal files, temporary exports, or editor configuration unless they are intentionally part of the repository.

### **Suggested naming examples**

```text
01-presentation.md
02-requirements-development-and-software-solution-design.md
03-solution-ui-ux-design.md
04-product-implementation-and-validation.md
assets/av1/interviews/
assets/tb1/mobile-mockups/
assets/av2/validation/
```

If the repository already uses a different naming structure, preserve that structure instead of renaming files without team approval.

---

## **Markdown and Documentation Rules**

- Keep heading levels consistent.
- Do not skip heading levels without a structural reason.
- Use descriptive `alt` text for every meaningful image.
- Use tables only when they improve readability.
- Keep image widths and alignment consistent with the report style.
- Verify that internal anchors work after changing headings.
- Use English terminology where required by the report.
- Avoid incorrect hybrid terms or informal software-engineering vocabulary in formal report content.
- Keep references and citations consistent with APA 7 requirements established for the project.

---

## **Collaboration Rules**

- All members must contribute to the report.
- Communicate before editing shared sections.
- Prefer one active branch per task.
- Do not reuse another member's branch for unrelated work.
- Review teammates' Pull Requests carefully.
- Resolve disagreements through the Pull Request discussion or team communication channel.
- Keep the Version Record consistent with meaningful report changes.
- Keep Collaboration Insights consistent with actual GitHub evidence.
- The author shown in Git commits must match the person who performed the contribution.
- Do not rewrite or squash another member's authorship in a way that removes required collaboration evidence.

---

## **Conflict Resolution**

If a conflict occurs:

1. Update the branch with the latest `develop`.
2. Identify which version of the shared content is correct.
3. Coordinate with the teammate responsible for the conflicting section.
4. Resolve the conflict manually.
5. Re-render or review the affected Markdown section.
6. Verify links, tables, and image paths.
7. Commit the conflict resolution with a clear message.
8. Push the corrected branch.

Example:

```bash
git fetch origin
git rebase origin/develop
```

After resolving files:

```bash
git add .
git rebase --continue
```

If the team is using merge instead of rebase for that case, document the resolution clearly in the Pull Request.

---

## **Protected Branch Rules**

Recommended repository protections:

### `main`

- Direct pushes disabled.
- Pull Request required.
- At least 1 approval required.
- Conversations must be resolved before merge.
- Force pushes disabled.
- Branch deletion disabled.

### `develop`

- Direct pushes disabled.
- Pull Request required.
- At least 1 approval required.
- Force pushes disabled.

These protections help preserve individual contribution evidence and prevent accidental changes to delivered versions.

---

## **Evaluation Evidence**

The repository must preserve evidence of collaborative work, including:

- Commits from every team member.
- Feature branches.
- Pull Requests.
- Pull Request reviews.
- Release branches and tags.
- Collaboration analytics.
- Consistency between GitHub evidence, the Version Record, Sprint Collaboration Insights, and the report.

Do not wait until the end of a delivery to generate artificial contribution evidence. Contributions should reflect the actual work completed throughout the milestone.

---

## **Language Convention**

Use **English** for:

- Branch names.
- Commit messages.
- Pull Request titles.
- File names.
- Technical identifiers.

Use the language required by the report for narrative content while preserving the official English names of software engineering concepts, artifacts, frameworks, technologies, and sections when applicable.

---

## **Final Checklist Before Requesting a Merge**

- [ ] I worked from the latest `develop`.
- [ ] My branch follows the naming convention.
- [ ] My commits follow Conventional Commits.
- [ ] I only changed files related to my task.
- [ ] The report section renders correctly.
- [ ] Images and hyperlinks work.
- [ ] Tables and headings are consistent.
- [ ] My contribution is traceable in Git history.
- [ ] I updated related evidence when required.
- [ ] I opened a Pull Request to `develop`.
- [ ] I requested at least one teammate review.
