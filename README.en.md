English · [Русский](README.md)

# You have read all five books about power and people — and when the moment comes, not one principle surfaces

The situation is laid out as a power map, three to five of the 176 principles from Greene's five
books are picked for that specific map, and every move carries an address: the book, the law, the
block of the digest.

```
claude plugin marketplace add https://github.com/beCyborg/jadlis-start.git
claude plugin install robert-greene@jadlis
```

No keys and no subscriptions beyond Claude Code itself, and the plugin never goes online — the
digests of all five books ship inside it; there is one setting, the memory folder, and without it
the advisor still answers, it just remembers nothing from previous sessions.

![The situation is laid out as a power map, and every recommendation points by tag at a specific block of the digest](docs/img/hero-jadlis-robert-greene.webp)

In words: on the left, the situation in your own words; in the middle, the power map — who holds
what and what drives them; on the right, three to five moves, each carrying a tag like `[48LP:L1]`
with the address of its principle.

This is my workbench published as it is, not a product: whatever I stopped using, I removed.

## Before → after

| By hand | With an AI chat | With this plugin |
|---|---|---|
| **Finding the principle you need.** The books sit on the shelf; the situation happens on a Monday morning. | It answers from a general memory of all the books at once, so you get an averaged retelling. | The kind of situation loads at most two digest files, and three to five principles are picked out of them. |
| **Where the advice came from.** The wording stays with you; the book and the number of the law do not. | It sounds like Greene, and there is nothing to check it against. | Every recommendation carries a tag like `[48LP:L1]` — the address of a block in a digest sitting on your own disk. |
| **What a law does not cover.** A law is remembered without the caveats where it fails. | It does not offer the caveats until you ask about them separately. | Each principle in the digest carries AVOID WHEN and a Reversal, and the reversal is required in the answer. |
| **The other side's move.** You count your own moves and guess theirs by mood. | It analyses your position, because your position is what you asked about. | A separate step applies the same principles to your opponent, and the fallback plan lands there too. |
| **What is left after the conversation.** The conversation ends, and later you cannot recall which move you chose or why. | A new session starts from a blank page. | The memory folder holds a profile, a map of players under codes, active strategies and lessons with outcomes. |

## How it works

![The situation goes into a power map, then into principle selection with tags, then moves, counter-analysis and a line into memory](docs/img/how-jadlis-robert-greene.webp)

Going in — the situation in your own words: who is involved, what your position is, what you want
and what you will not do.
Inside — four steps in a row: the power and emotion map, three to five principles picked with tags,
moves with a historical example and a risk, counter-analysis from the opponent's side.
Coming out — an answer where every move names its source, and a line written into the memory file.

In words: situation → power and emotion map → at most two digests → three to five tagged principles
→ moves with example, risk and timing → reversal, the opponent's move and a plan B → a line into
memory.

The advisor reads six digest files: power and influence, persuasion, strategy and conflict, mastery,
human nature, and cross-book patterns. A routing table sets the path — kind of situation → primary
file → backup — and no more than two files are loaded per query. Inside sit all 48 laws of power,
all 33 strategies of war, all 18 laws of human nature, the characters and steps of The Art of
Seduction and the chapters of Mastery: 176 principles, each with its own address.

A tag is the address of a block inside the plugin, not a reference to a page of a book: the digests
were written anew, they carry no verbatim excerpts, and their examples age along with the books —
that is stated in `NOTICE.md`. The lens is the author's and it is not softened: the skill
is instructed to describe how power works rather than how it ought to, and to add no moral caveats
that the author himself does not make; when you are the one being manipulated, it walks through the
signs.

[уточнить] — the repository holds no command or script that checks whether a tag exists in the
digests.

## Installing and the first run

**a) Text to paste to an agent.** Copy the whole thing into a Claude Code chat:

```
You are the installer. Install the plugin robert-greene from the jadlis marketplace on this Mac.
Run exactly these commands, verbatim, shortening nothing:
1. claude plugin marketplace add https://github.com/beCyborg/jadlis-start.git
2. claude plugin install robert-greene@jadlis
3. claude plugin list — show me the line about robert-greene and its version.
This plugin needs no keys and no external binaries. There is one setting, the memory folder
MEMORY_DIR: ask me for the path, show me where it was written, and stop there. Do not read the
contents of that folder and do not copy it anywhere.
Before each command show it to me in full and wait for "yes". If I say "no", do not run it,
tell me what you skipped, and move on.
If a command returns an error, stop, show me the output, and do not move to the next one.
```

**b) Commands by hand.**

```
claude plugin marketplace add https://github.com/beCyborg/jadlis-start.git
claude plugin install robert-greene@jadlis
claude plugin list
```

The first command installs nothing — it adds the marketplace. Only the second one installs, and one
line removes it: `claude plugin uninstall robert-greene@jadlis --keep-data`.

The memory folder can be set during the install — `claude plugin install robert-greene@jadlis
--config MEMORY_DIR=~/advisors-memory` — or later: `/plugin` → robert-greene → settings →
`MEMORY_DIR`. On an already installed plugin the `--config` flag silently changes nothing, so
changing the path through it means reinstalling (checked 2026-09-07). The default is
`~/advisors-memory`; the setting is optional, and without it the advisor answers and says it will
not remember the session. The folder skeleton is unpacked on the first run and never touches
existing files; the folder is shared with the other Jadlis advisors, and this one's profile is
`Профили/green-advisor.md`.

**c) The short command.** Open Claude Code in the folder you work in and type:

```
/robert-greene <the situation>
```

If it is not found, check the name with `claude plugin list`. Describe the situation in your own
words: who is involved, what each of them holds, what you want and what you are not prepared to do;
without the players and the balance of power the answer comes out generic — that is a limit of the
method, not forgetfulness of the plugin.

## Limits, cost, updating

**What it does not do.** It does not convene a council of lenses and does not run sceptics over the
claims — that is `advisor-decision` and its neighbours; here you get one author's lens without
averaging. It does not cross-verify claims and does not go online: it holds no fresh data about your
market or your people. It does not replace a lawyer, a doctor or a therapist and carries no
consequences: the decision and the responsibility stay with you. It does not quote the books — what
ships inside are derivative digests, and the rights to the source texts belong to their authors and
publishers (`NOTICE.md`). And it does not accept edits to this repository: it is
generated from a private source and CI compares the hash against `SHARED_FROM.txt`, so a direct edit
turns the build red — open an issue here, the change lands in the source.

**What you need.** No keys, no paid subscriptions beyond Claude Code itself, no external binaries.
The only setting is `MEMORY_DIR`, an ordinary folder of markdown files on your disk; it is private —
players, strategies and outcomes settle there — so it does not belong in a public git repository.

**How tokens get spent.** A run is light: one skill, no subagent fan-out; at most two digest files
are loaded per query and the rest stay untouched. The costlier case is a long situation with many
players — that grows the input, not the number of calls.

**Verified where I work:** my Mac, my subscription. Where else this works — [уточнить].

**Terms of use.** There is no license: all rights reserved by the author. You may read it and use it
personally. Commercial use, republishing and bundling it into your own products — by arrangement
with me.

**Updating.** With a third-party marketplace, auto-update is off on your side: until you run the
first command you keep the version you installed.

```
claude plugin marketplace update jadlis
claude plugin update robert-greene@jadlis
claude plugin list
```

Reinstall, if something ended up crooked:

```
claude plugin uninstall robert-greene@jadlis --keep-data && claude plugin install robert-greene@jadlis
```
