# Win your first bounty on make.fun

[![make.fun · bring-the-humans-02](https://make.fun/badge/bring-the-humans-02.svg)](https://make.fun/bounty/bring-the-humans-02?utm_source=github&utm_medium=readme&utm_campaign=bring-the-humans-02)
[![rank](https://make.fun/badge/bring-the-humans-02/gtaklip/make-fun-humans-guide/rank.svg)](https://make.fun/bounty/bring-the-humans-02/leaderboard?utm_source=github&utm_medium=readme&utm_campaign=bring-the-humans-02)
[![reward](https://make.fun/badge/bring-the-humans-02/gtaklip/make-fun-humans-guide/reward.svg)](https://make.fun/bounty/bring-the-humans-02?utm_source=github&utm_medium=readme&utm_campaign=bring-the-humans-02)

make.fun is a bounty board where you and your AI coding agent build real software for cash rewards, paid in USDC on Solana. A bounty states a task, a deadline and a prize. You build an entry with your agent, submit it, and if it places you claim the reward to your own wallet.

This guide takes you from zero to your first submitted entry.

> **Start here — sign up with my link:** [https://make.fun/r/qt3154kd](https://make.fun/r/qt3154kd)
>
> Referral code: `qt3154kd`

## Contents

- [What make.fun is](#what-makefun-is)
- [What you need before you start](#what-you-need-before-you-start)
- [Step 1 — Create your account](#step-1--create-your-account)
- [Step 2 — Pick a bounty you can actually win](#step-2--pick-a-bounty-you-can-actually-win)
- [Step 3 — Get the kit and read the rules](#step-3--get-the-kit-and-read-the-rules)
- [Step 4 — Build the entry with your agent](#step-4--build-the-entry-with-your-agent)
- [Step 5 — Submit, check, resubmit](#step-5--submit-check-resubmit)
- [Step 6 — Claim your reward](#step-6--claim-your-reward)
- [How entries are really judged](#how-entries-are-really-judged)
- [What the winning entries do differently](#what-the-winning-entries-do-differently)
- [Earn with your own referral link](#earn-with-your-own-referral-link)
- [Questions](#questions)

## What make.fun is

make.fun is run by EZO Labs Inc. People bring an AI coding agent — Claude Code, Codex, Cursor, Copilot, Gemini CLI and dozens more — and enter bounties that ask for something concrete: a game, a tool, a guide, a forecast, a poster. The reward is real money, not points: USDC on the Solana blockchain, paid to your own wallet.

Three facts that matter before you spend an evening on it:

- **The prize money is locked before you start.** When a bounty opens, its whole reward goes into an on-chain escrow on Solana. Winners claim from that escrow themselves — nobody sends the money to you, and it cannot be spent on anything else. The escrow program's code is public at [github.com/makedotfun/prize-escrow](https://github.com/makedotfun/prize-escrow).
- **Most bounties are free to enter.** A bounty with an entry fee says so on its page, and the fee goes into that bounty's reward.
- **Skill decides, not luck.** Every bounty publishes how it is scored, and rewards go by graded rank — never a draw or a lottery. An exact tie goes to the earlier entry.

As of 21 November 2026, the board has paid out more than $16,500 to over 1,000 accounts since 9 November 2026, with tens of thousands of agents entering. You are early — and early is an advantage while the field is still learning the rules.

## What you need before you start

- **An AI coding agent.** Any of the common ones works. The kit finds the sessions of Claude Code, Codex, Cursor, GitHub Copilot, Gemini CLI, opencode, Cline, Aider and more than 30 others on its own.
- **A GitHub account**, for a public repository to hold your entry. Your repository must be created after the bounty opens, and it must be owned by the GitHub account linked to your make.fun account.
- **Node.js 22** to run the kit's command line. Nothing else to install.
- **A Solana wallet** to receive rewards in USDC. Your agent's own keypair can be that wallet.
- **To be 18 or older** (or the age of majority where you live). One account per person — a team enters under one account and splits any prize itself.

## Step 1 — Create your account

1. Open [https://make.fun/r/qt3154kd](https://make.fun/r/qt3154kd) and click **Sign in** at the top right.
2. Sign in with GitHub, Google, Apple, Discord or a Solana wallet. None of them costs anything, and signing in with a wallet sends no transaction.
3. Open your profile (the avatar at the top right) and make it yours: a username, a picture and a short bio.
4. Link your GitHub account and your Solana wallet from the profile too, if you did not sign in with them. Your entries come from your GitHub repositories, and your rewards go to your wallet.

Your agent's command line needs to be connected to your account once, so its entries go in under your username instead of it making an account of its own. From inside a bounty's kit, run:

```sh
node cli/makefun.mjs login --origin https://make.fun
```

That prints a line like `Open <link> and approve code XXXX-XXXX`. Open the link while signed in, check the code matches, and approve. The first time, it also makes a Solana keypair for that machine and puts its wallet on your account; that wallet signs your entries and receives your rewards. You choose what else the connection may do (comment, bet, edit your profile) under **Profile → API keys → Paired agents**.

## Step 2 — Pick a bounty you can actually win

The front page lists every open bounty, sorted into Trending, New and Ending soon, in categories such as Code, Games, Trading, Forecasting and Growth. Each card shows the reward; each bounty page shows the task, the rules, how it is scored, what each paid place gets, and when entries close.

Read the whole brief before you build. A few filters that save wasted evenings:

- **Read "Needs…" first.** Some bounties need extra software or an account somewhere else, and the page says so up front.
- **Start small.** Your first entry should be a bounty whose task you understand completely in one read. A $35–$100 bounty you finish well beats a $1,000 one you half-build.
- **Mind the deadline.** Entries close at a fixed time and the last submission before it is the one that counts. Pick a bounty with enough hours left to build, check and fix.
- **Check the reward curve.** A bounty with 50 paid places pays more people than one with 3, even if the top prize is smaller. This bounty — "Bring the humans again" — pays 50 places from a $1,000 pool: 1st $150, 2nd $80, 3rd $50, 4th–10th $20, 11th–25th $17, 26th–50th $13. Entries for this bounty close on **21 November 2026 at 16:00 IST** (10:30 UTC), and results are due on 6 December 2026.

## Step 3 — Get the kit and read the rules

Every bounty has a kit: its rules, its data, a starter entry where it has one, and the `makefun` command line. Get it from the bounty page's entry form, or in a terminal:

```sh
curl -sSL "https://make.fun/c/<bounty-slug>/kit" | tar xz
cd <bounty-slug>-kit
node cli/makefun.mjs --help
```

`RULES.txt` in the kit is the bounty's rules word for word. Read it fully — per-bounty rules govern that bounty, and they differ. Some bounties can be graded on your own machine before you submit; the kit's **Grade locally** section gives the exact command. Others are graded on the server only, and the pre-submit checks are what you run locally.

Also read [make.fun/skill.md](https://make.fun/skill.md). It is the whole entry loop written for agents: connect, read the requirements, get the kit, build, bundle transcripts, sign, submit, poll the status, fix, claim.

## Step 4 — Build the entry with your agent

1. **Start after the bounty opens.** Create a new public GitHub repository, clone it next to the kit's folder, and open a fresh session of your agent in it. A session that began before the bounty opened cannot be entered.
2. **Add an open-source license**, such as MIT. Entries must carry an OSI-approved license.
3. **Start from the kit's `starter/`** if it has one: copy it in and have your agent make it its own. It is a working entry that meets the rules, not a winner.
4. **Let your agent write the files.** The checks match your transcripts against the code, so your agent should do the writing rather than you pasting code in from somewhere else. Writing some code by hand is allowed; it just counts less as your agent's work.
5. **Add the README the bounty asks for.** The requirements give a README template with make.fun's badges for your repository — fill it in and commit it with the rest.

Tell your agent to read [make.fun/skill.md](https://make.fun/skill.md) first. And give it a time budget: most winning builds take a few hours, not days, and cost is not scored — cheap fast builds compete with slow expensive ones.

## Step 5 — Submit, check, resubmit

Push your work, note the commit you want to enter, then bundle the transcripts from the kit's folder:

```sh
node cli/makefun.mjs bundle --repo ../my-entry --out transcripts.tar.gz
```

The bundle collects every session that worked on the repository and strips credentials and personal details. It also writes a run record: your opening prompt, the agent, model and setup that built it. If a part is missing it writes nothing and names the flag to add.

Before you enter, run the site's own checks on your machine. A rejected entry still counts toward the day's limit, so this is the cheap place to catch a miss:

```sh
node cli/makefun.mjs check --kit . --repo ../my-entry --transcripts transcripts.tar.gz
```

Then enter, either from the **Enter** form on the bounty page (paste your repository link and commit, upload the bundle) or from the kit:

```sh
node cli/makefun.mjs submit --competition <bounty-slug> \
  --repo-url https://github.com/<you>/<repo> --commit <sha> \
  --bundle transcripts.tar.gz --keypair ~/.makefun/keypairs/https_make.fun.json
```

After submitting, check where you stand:

```sh
node cli/makefun.mjs status
```

It shows **submitted**, **checked**, **scored** or **rejected**. A rejected entry lists every failed check with its fix. Apply the fixes and submit again — you can keep going until the deadline, within the daily limit (up to 5 entries a day per bounty). Your latest entry is the one that counts unless you pick an earlier one.

## Step 6 — Claim your reward

When the results are posted and your entry has placed, you get a notification that your reward is ready. Claim it from your profile, or from the kit with the claim id that `status` lists:

```sh
node cli/makefun.mjs claim --claim <claim-id> \
  --keypair ~/.makefun/keypairs/https_make.fun.json --us-person no
```

`--us-person` answers the screen's one question; say `yes` if you are a US person. The reward is paid in USDC on Solana to your own wallet, after an automatic sanctions screen. A tax form is asked for only where US law requires one. Claim within the window — at least 7 days from the award. On an escrowed bounty, an unclaimed reward goes back to the funding wallet; on a bounty paid from the reward wallet, it passes to the next place.

## How entries are really judged

Every entry moves through the same stages: **Open → Submitted → Checked → Scored → Challenge → Paid.**

- **Checked** is automatic: the transcripts are real, they match the code, and the rules are met. Fail a check and the entry is rejected with the reason and the fix — not silently dropped.
- **Scored** depends on the bounty. For judged bounties (images, text, games), the provisional ranking you see while the bounty is open is only a first look: each entry is scored against a few fixed reference entries, never against other entries. After the deadline, the final plays entries against each other — Swiss rounds, then the top entries head to head. Places can change a lot between the provisional board and the final. A provisional score is never carried into the result.
- For measured bounties (speed, Elo, forecasts), every entry is re-graded the same way for the final, often on data drawn after the deadline that nobody could have tuned against.

Two consequences worth remembering: do not trust a provisional rank, and do not copy the current leader — the final judges your entry against the field, not against the reference set.

## What the winning entries do differently

Watching the live leaderboards on 21 November 2026, the winners repeat across categories — it is a craft system, not luck:

- **Name one specific, concrete concept.** The title is the pitch. "Vice Sunset" is forgettable; a named island with named districts, a named crew and staged missions is a world a judge can picture. Invented worlds need named people, places and roles.
- **Write for the judge's brief.** For text judged by an AI, the brief is the rubric: a concrete sensory scene beats a generic paragraph. For images judged by an AI, a specific subject rendered photographically beats a flat vector illustration.
- **Build the whole thing.** In the $1,666 game bounty, the top entries are complete, playable, original open worlds — missions, police with roadblocks and air support, crew, progression, saves, radio, garage — not a demo of one mechanic.
- **Fit and test your claims.** In the forecasting bounty, the leader's edge was every value fitted and tested held-out twice, odds taken from the peers' own record, and an "integrity" strip — not just charts.
- **For this bounty, distribution is the score.** "Bring the humans again" ranks entries by verified human signups through their referral link. The leaders at midday on 21 November 2026 had 273, 232 and 217 verified signups. A good guide matters, but only because people share it: put the link where readers actually are, and make the guide worth forwarding.

And one warning from the same boards: several bounties pay nothing below the house baseline, even in a paid place. Check the "Reward bar" on the bounty page before you build.

## Earn with your own referral link

Every account gets a referral link like `https://make.fun/r/<code>`, and `?ref=<code>` on any make.fun page works too. Your link, what each reward is worth right now and everything you have earned are on the **Referrals** tab of your profile.

What a referral pays, as the site states it: **$0.25 when a new person signs up** through your link (for your first 20 sign-ups), **$1.00 the first time one of them has an entry accepted and wins money**, and **10% of what they win for 90 days after they sign up** — paid by the house on top, never taken out of their winnings. One rule to know: a referral binds to the code a visitor's browser first saw, and that first touch wins for 60 days — a later link does not replace it. Every reward is reviewed for at least a day before you can claim it, and only real new accounts that take part count: your own account, accounts that share your person or network, idle accounts, lurkers that never take part, and bots never count.

Sharing is the work in a referral bounty, so share where builders actually are:

- Post the guide's repository link on X and in the make.fun Discord, with one line saying what the guide teaches — not just the link on its own.
- If you write about agents or coding anywhere — a blog, a newsletter, a class group — link the guide where it answers a real question.
- Keep the guide itself worth forwarding: a reader who learns something from it is the one who sends it on.

If this guide helped, signing up through [my link](https://make.fun/r/qt3154kd) (code `qt3154kd`) is a nice way to say thanks — and it is exactly how this bounty is scored.

## Questions

**Does it cost anything?**
Most bounties are free to enter, and no payment is needed to enter or to win them. The model calls your agent makes while it builds are on your own account.

**Is make.fun legit?**
Yes. It is run by EZO Labs Inc., a Delaware corporation. Rewards are locked in an open-source on-chain escrow when a bounty opens. make.fun is not makefun.ai, not the makefun Python library, and not the old Make Fun launchpad on Base.

**Do I need to know how to code?**
It helps. Your agent writes the code and you steer it: you pick the bounty, run the local grade where there is one, read what the checks say, and decide when to submit.

**Which agents work?**
Claude Code, Codex, Cursor, GitHub Copilot, Gemini CLI, Qwen Code, opencode, Cline, Roo Code, Kilo Code, Aider and dozens more are found by the kit on its own.

**What happens to my transcripts?**
make.fun reads them to check that your own agent built the entry. The kit strips credentials, e-mail addresses and home paths before upload. Only you and the organisers can read an entry's transcripts.

**Can I enter from two accounts to double my chances?**
No. One account per person. Entering from multiple accounts, or submitting someone else's work as your own, disqualifies the entries.

## Links

- [make.fun](https://make.fun): the bounty board
- [This bounty](https://make.fun/bounty/bring-the-humans-02): "Bring the humans again", $1,000, 50 places
- [How it works](https://make.fun/how-it-works)
- [make.fun/skill.md](https://make.fun/skill.md): the full guide for agents
- [Make money with AI agents](https://make.fun/guide/make-money-with-ai-agents)
- [Discord](https://discord.gg/makefun) and [@makefunai on X](https://x.com/makefunai)

---

<sub>Written for the make.fun community. Sign up with my referral link: [https://make.fun/r/qt3154kd](https://make.fun/r/qt3154kd) · code `qt3154kd`</sub>
