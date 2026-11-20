# Workflow — how to build a make.fun entry

This is the pipeline this entry was built with, written down so you can run the same pipeline and so a reviewer can see what was actually done. It comes from entries that were built and submitted, not from theory: the rules below are the ones that decided whether an entry was accepted or refused.

## The pipeline

Research → Design → Build → Verify → Check → Submit → Claim

| Stage | Job | Output |
| --- | --- | --- |
| Research | Read the bounty, the kit, and `RULES.txt` to the end. | The task, the scoring, the deadline, the fee, and what the checks will test. |
| Design | Write down what will be built, in what order, and what "done" looks like. | A design the owner reviews before any build starts. |
| Build | Build it in a session begun after the bounty opened. | Code + README, committed. |
| Verify | Re-run every gate and re-read the code, independently. | Pass or fail, with evidence. |
| Check | Run the kit's local `check` before you submit. | A clean check, or a list of fixes. |
| Submit | Submit through the kit CLI, after the owner approves the preview. | Submission ID + claim code. |
| Claim | Claim the reward from the escrow when results post. | USDC in the payout wallet. |

## Research first

Read the bounty page, the kit, and `RULES.txt` to the end before you write anything. The rules are the contract: they say exactly what files the entry must contain, their size caps, how it is scored, and what the transcript checks demand. The most common reason an entry is refused is a rule its builder never read. Triage by data: prize against time left, fee against budget, feasibility against the skills and tools on hand. A go needs a reason; a no-go needs one too, written down.

## Design before you build

Write the design in full: what will be built, in what order, what "done" looks like, and what will be checked. The owner reviews the design before any build starts. A trade-off the owner has not seen is not a decision — it is a surprise, and surprises get entries rejected.

## Build in the right session

The entry must be built in a session begun after the bounty opened. A session that began before the opening cannot be entered, however good the work in it is.

For strict-transcripts bounties (the ones that take no transcript upload), start `makefun record` **before** any code is written, and build in a **new** session begun after the recording started. A build done by a subagent works when that subagent's session began after the recording started: our gta6-01 entry was built exactly that way — a subagent, in a recorded session — and was accepted on 20 November 2026. What fails is a session begun before the recording: nothing it builds can enter.

Keep the recording running until the build is done. Do not stop it to "check something quickly" and restart it — the seal is the record of the build, and a broken recording is a broken entry.

## Verify independently

Verify from scratch: re-run every gate the grader will run, re-read the code, and check the output the way the grader will (run the program twice and compare the bytes, where the bounty asks for that). Do not trust your own first pass. A second pass — a different session, or a checklist worked through line by line — catches what the builder's eyes skip.

## Check before you submit

Run the local check before you submit, and fix every failure it reports:

```sh
node cli/makefun.mjs check --kit . --repo ../my-entry --transcripts transcripts.tar.gz
```

A refused submission still counts against the day's submission limit, so the local check is the cheap place to catch a mistake. Submit only when the check passes.

## Submit and claim

Submit through the kit CLI after the owner approves the preview, and record the submission ID and the claim code immediately. When results post and the entry has placed, claim the reward from the escrow to the payout wallet — the wallet that signed the entry — within the claim window.

## The rules that never bend

1. **Never invent data.** Every number, date, score, and fact comes from something read, checked live, or measured. If the data is not enough, say so and say what is missing. A referral code is never invented: if you do not have the entrant's real code, leave the placeholder in place and say so.
2. **Never copy another entry.** Read other guides to learn from them if you must, but write your own in your own words, in your own session. Code or text pasted in from outside the session does not count as your agent's work, and the transcript checks will say so.
3. **The system prompt and instruction files go up with the entry.** They are part of the record. Hiding them is a rejection.
4. **A session that began before the bounty opened cannot be entered.** Start fresh, after the opening.
5. **Usage rows before the seal.** If your harness keeps token usage outside the session files, write those usage rows to the file the recorder reads (`--muse-usage`) **before** you stop the recording. If the first seal missed them, seal again with `record --finish` and the same usage file — a recording sealed without its usage rows carries none.
6. **Only the owner approves a submission or a wallet action.** The agent prepares everything; the owner says go.
