---
name: batch-subagent-workflow
description: Coordinate and verify parallel processing of many literature files in pending using bounded subagent assignments, explicit ownership, source-based review, and controlled integration. Use when a batch is being processed in subagent mode, without depending on a particular agent framework.
---

# Batch Subagent Workflow

## Scope and Shared Rules

Read the collection's [main skill](../../SKILL.md) before planning a batch. Use [Markdown Usage](../markdown-usage/SKILL.md) for note composition and presentation. The collection root is the directory containing the main skill, not this auxiliary skill's directory. All agents must respect the collection structure, scientific standards, language requirements, and read-only status of `skills/`.

This skill describes responsibilities, task boundaries, handoffs, and acceptance criteria. It prescribes no agent API, messaging format, isolation mechanism, model, or fixed number of workers. Apply it when subagent work is authorized and available; it does not itself require enabling subagents. The same boundaries can be followed sequentially when parallel execution is unavailable.

The goal is a batch of verified, integrated notes, not merely a collection of completed agent responses. Every assigned source must have an explicit outcome, and every completed note must meet the main skill's requirements.

## Roles and Ownership

Use three logical roles. One agent may perform more than one role when appropriate, but responsibility must remain explicit.

| Role | Responsibility | Write scope |
| --- | --- | --- |
| Coordinator | Inventory, grouping, assignment, progress tracking, conflict resolution, integration, and final reconciliation | Batch records, controlled source archival, and the global index; note edits only after ownership is handed over |
| Worker | Read assigned originals, produce a complete note and its assets, perform a source-based self-review, and report evidence and gaps | Only the assigned note directory or designated working output |
| Reviewer | Check the actual note against the originals and acceptance criteria; identify concrete defects | Review findings by default; note changes only after an explicit ownership handoff |

Maintain one active writer per note directory. Workers may read the main skill, auxiliary skills, index, and relevant existing notes but must not modify shared instructions, other workers' outputs, or the global index. Reviewers must not silently edit a note while its worker is revising it.

The coordinator owns updates to `index.md` and moves of original files from `pending/` into `source/`. These steps are serialized even when analysis runs in parallel. Centralizing these mutations prevents competing index rewrites and disappearing inputs. If responsibilities are transferred, record the transfer before another agent writes.

## Inventory and Work Units

Before dispatch, inventory the batch scope and inspect the existing index and note directories. Record each input's root-relative path, apparent work identity, available version, accessibility, and existing-note match where known. Do not identify a paper solely from its filename. Keep unreadable or uncertain inputs visible in the inventory.

Use one intellectual work and its associated original files as the default unit: a main paper, its appendix, and its supplement normally belong to one task. Do not assign them independently and create duplicate notes. Distinguish exact duplicate files from revised versions and merely similar titles; do not silently delete duplicates or combine substantively different works.

Reserve a unique descriptive note directory before dispatch. Check for collisions with existing directories and with other assignments. When an existing note describes the same work, decide whether the task is an update, a version comparison, or already satisfied, based on the user request and the evidence. Preserve existing user edits and do not overwrite a note merely because its directory name matches.

Record the initial batch boundary. Newly arriving files can enter a later explicit batch or be added deliberately to the current inventory; do not let a changing directory listing make completion impossible to measure.

## Decomposition and Scheduling

Prefer parallelism across independent papers. Assign each worker responsibility for a coherent note so that motivation, methods, experiments, and limitations remain connected. Avoid distributing individual headings of a routine paper among different writers; the resulting fragments often duplicate context and disconnect conclusions from evidence.

For an unusually large or complex work, bounded subtasks may cover appendix extraction, experimental evidence, reference verification, or asset preparation. Give each subtask a precise scope and an evidence-bearing deliverable. Keep one synthesis owner responsible for reading enough of the original to integrate the results, resolve contradictions, and produce the final note. Supporting agents must not concurrently write the same `note.md`.

Estimate effort from the actual material: length, extraction quality, mathematical density, number of experiments, supplementary files, and available resources. Balance assignments by expected effort rather than file count alone. A small group of related short works may share a worker, but keep separate per-work status and acceptance decisions.

Use bounded waves sized to the available execution and review capacity. Inspect an early completed note to confirm common conventions before expanding a large batch. If a systematic misunderstanding appears, correct the shared assignment guidance and identify already produced notes affected by it; do not edit the read-only skill library to communicate the correction.

Keep most work independent. A pending related note need not block analysis: use verified bibliographic information until its final path is accepted, then resolve internal links during integration. Only make a task dependent on another when it actually requires that task's evidence or artifact.

## Assignment Brief

Each assignment must be understandable without relying on an agent's access to the coordinator's conversation history. Include:

- **Identity and inputs:** Task identifier, the work being processed, exact source paths, relevant versions, and associated appendices or supplements.
- **Deliverable and boundaries:** Reserved note path, asset location, permitted edits, source files to treat as read-only during analysis, and shared files the worker must not change.
- **Context and standards:** Main and relevant auxiliary skill locations, requested body language, scope and level of detail, and any user-specific requirements.
- **Evidence expectations:** Source locators for important claims, experiments, figures, and references; explicit separation of reported findings and independent analysis.
- **Dependencies and uncertainties:** Existing related notes, unavailable resources, known ambiguities, and the condition that requires reporting a blocker rather than guessing.
- **Completion contract:** Required self-review, the expected handoff contents, and the fact that submission is subject to review and integration.

Do not give several workers an unbounded instruction to process anything they find in `pending/`. Claim and assign inputs before work starts so that two workers do not process the same file unknowingly.

## Progress and Handoff

Maintain a compact batch record in the available coordination mechanism or an appropriate working location outside `skills/`. No specific file format or new permanent collection directory is required. Track task identity, source paths, output path, current owner, state, dependencies, review outcome, unresolved issues, and integration status. Preserve enough information to resume work after interruption.

Use a state model with distinctions equivalent to these:

| State | Meaning and transition evidence |
| --- | --- |
| Queued | Inventoried and scoped, with no active worker |
| In progress | An identified worker owns the assignment |
| Submitted | Deliverables exist and the worker has supplied a self-review and handoff |
| Needs revision | Review found concrete defects; an identified owner must address them |
| Accepted | Content and evidence checks passed for the reviewed revision |
| Integrated | Originals are archived, the index is updated, and final paths and links are checked |
| Blocked | A specific unresolved condition prevents completion; the next required action is recorded |
| Excluded | Deliberately outside processing scope or already satisfied, with an explicit reason |

Do not treat a submitted message, a present file, or a worker's confidence as proof of completion. If a worker is interrupted, inspect its actual artifacts before resuming or reassigning it. Prevent the previous owner from continuing to write before handing the path to a replacement.

A worker's handoff should identify the source files actually read, output files created or changed, key source locators, checks performed, inaccessible resources, remaining uncertainties, and proposed index metadata. Supporting subtasks should return evidence with context, not unsupported conclusions. Keep operational review notes out of the finished scientific narrative unless they express a relevant evidence limitation.

## Review and Revision

Every note requires a source-based self-review and an acceptance review before integration. Prefer a separate reviewer for independent assessment when available; otherwise perform an explicit second pass and do not describe it as independent review. Reviewer access must include the actual source material and final candidate note, not only the worker's summary.

Check every note against the following criteria:

1. **Identity and coverage:** Verify the work, version, title, source context, background, applicable methods and experiments, conclusions, independent limitations analysis, and relevant references. Confirm associated appendices were considered where needed.
2. **Scientific fidelity:** Check factual claims against source evidence, especially numerical results, metric direction, dataset splits, baselines, resource requirements, publication status, and limitations. Check every reported number and quotation, not just a convenient example. Do not accept citation formatting as verification of a citation's contents.
3. **Reasoning:** Confirm conclusions follow from the reported conditions and uncertainty. Distinguish author statements, interpretations, and proposed improvements. Look for critiques contradicted by the original's appendix or for invented evidence filling a missing detail.
4. **Composition:** Check English headings, requested body language, connected prose, sufficient experimental detail, restrained formatting, and horizontal layout. A matching heading outline alone is insufficient.
5. **Assets and links:** Verify media provenance, legibility, source locators, relative links, and the intended final locations. Before archival, check planned source links against the assigned originals; repeat existence checks after the move.
6. **Scope and integrity:** Confirm edits stayed within the assignment, other notes and skills were not changed, original files remain accounted for, and the candidate contains no unfinished instructional placeholders.

For defects, provide the affected file or passage, the contradictory or missing evidence, the required correction, and its priority. Return factual errors, missing required analysis, or source mismatches for revision rather than hiding them behind a generally positive assessment. Record unavailable verification explicitly; do not claim a fact was checked when its source could not be read.

After revision, verify the fixes and any dependent claims, tables, figures, and conclusions. Do not repeat unrelated checks without a reason, but invalidate earlier acceptance when subsequent changes affect its basis. Resolve reviewer disagreement by inspecting evidence and retaining justified uncertainty, not by voting or accepting the more confident agent.

## Controlled Integration

Integrate accepted notes in a controlled sequence. The coordinator verifies the final destination, preserves unrelated existing content, and moves the assigned originals into the note's `source/` only when they are no longer needed at their pending paths by active tasks. Confirm destination existence and file integrity before treating archival as complete; never overwrite a different original with the same filename.

Update the current global index without losing entries added since dispatch. Use accepted metadata, avoid duplicate entries, and prefer links to accepted related notes where available. Resolve cross-note references using actual final paths rather than planned names that may have changed.

Then check the final `note.md`, assets, archived originals, index entry, and relative links together. Mark the task integrated only after these checks pass. Review and archival are distinct: an accepted draft with originals still in `pending/` is not fully processed.

If interruption occurs between moving a source and updating the index, record the actual state and resume from it. Inspect both source and destination before retrying so that a completed move is not mistaken for a missing input or repeated destructively. Keep failed or partial notes clearly tracked and do not publish them in the index as completed work.

## Batch Reconciliation and Completion Report

Reconcile the final result against the initial inventory, grouping files by work. Several files may correctly produce one note; compare explicit mappings rather than expecting file and note counts to match. Every original input must be accounted for as integrated, excluded with a reason, blocked, or still unfinished. Do not leave an assigned source untracked because its worker stopped responding.

Check batch-wide naming collisions, duplicate works, inconsistent language or terminology, missing index entries, orphaned assets, broken cross-note links, and unresolved review findings. Verify that integrated originals are present under the intended `source/` directories and that any remaining files in `pending/` have an explained status. Do not delete unexplained leftovers merely to make the batch look complete.

Report the number of works integrated and files accounted for, the locations of completed notes, and any blocked, excluded, or unfinished items with reasons. State material verification limits, including inaccessible sources or unavailable render previews. Claim complete processing only when all in-scope work is integrated and no required task remains; otherwise report partial completion precisely.

## Interpretation Reminder

Parallel execution changes responsibility and scheduling, not the required scientific quality. Clear ownership prevents overlapping writes; evidence-based review establishes correctness; final reconciliation establishes completeness. Delegation alone establishes none of these.
