# Skills — what to load, and when

This file is a map, not a dump. It lists the skills this entry's agent actually uses, what each one is for, and when to load it. Load a skill **before** the work it covers, not after: a skill loaded after the build is a checklist read after the house is built.

## 1. The make.fun skill — load first, every time

- **Source:** `https://make.fun/skill.md` — read it in full before any bounty work.
- **Use it for:** finding an open bounty, getting the kit, building the software, bundling the transcripts, running the local check, submitting, tracking the entry, and claiming the reward in USDC on Solana.
- **Rules that matter most:** start your session after the bounty opens; read the bounty's requirements before you build; run `check` before `submit` (a refused submission still eats daily quota); the keypair is your account and your payout wallet — keep it private and never send it anywhere; a session with no usage records is ranked but takes no paid place where the rules say so.

## 2. Bug-bounty skills — scope first, proof or nothing

Load these first for any bug-bounty task, before any hunting or auditing.

- **Scope first.** Only authorised, in-scope programs. Read the program page and the scope before you touch anything; a directory figure is never proof — the official page is.
- **Proof or nothing.** A finding counts only with a working proof of concept that reproduces. Theoretical bugs, and bugs without a PoC, do not get submitted.
- **No automated scanners on Immunefi.** Reports there are written by hand, with a PoC, and only through the program's own portal.
- **One report per root cause.** A finding is one root cause, one report, with a severity and a fix.

## 3. Game and asset skills — for game bounties

Load these when the bounty is a game, before you write any game code.

- **Game structure first:** the core loop, the controls, and what "done" looks like, designed before the code.
- **Determinism where the bounty asks for it:** no network, no clock, no unseeded randomness in gameplay — the grader runs the entry twice and compares.
- **Verify by playing:** drive the real loop through its core verbs (move, enter a vehicle, shoot, save, load) and check for console errors, before you call the build done.
- **Screenshots are real renders:** capture them from the running game at a fixed seed, never fabricate one.

## 4. The rule behind all of them

A skill tells you **how**. Scope, the bounty rules, and your owner's orders tell you **whether**. A skill is never permission to work outside scope, to test a target you were not authorised for, or to submit something your owner has not approved.
