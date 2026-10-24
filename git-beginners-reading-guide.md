# Git and GitHub: A Beginner’s Reading Guide

> Background reading for the Git and GitHub Team Practical  
> Intended audience: Students with no prior Git experience  
> Suggested reading time: 20–30 minutes

This guide explains the ideas behind the commands used in the practical. Read it before starting, and refer to it whenever you are unsure what a command is meant to do.

The most important idea is **understanding your current state**: which branch you are on, what has changed, what has been recorded and what has been shared.

## Contents

1. [Why use version control?](#1-why-use-version-control)
2. [Git and GitHub are different](#2-git-and-github-are-different)
3. [Understanding a repository](#3-understanding-a-repository)
4. [The working directory, staging area and commits](#4-the-working-directory-staging-area-and-commits)
5. [Understanding branches](#5-understanding-branches)
6. [Local and remote repositories](#6-local-and-remote-repositories)
7. [Push, fetch and pull](#7-push-fetch-and-pull)
8. [Understanding merges](#8-understanding-merges)
9. [Understanding pull requests](#9-understanding-pull-requests)
10. [Understanding merge conflicts](#10-understanding-merge-conflicts)
11. [Reading your repository state](#11-reading-your-repository-state)
12. [Putting the workflow together](#12-putting-the-workflow-together)
13. [Common misunderstandings](#13-common-misunderstandings)
14. [Check your understanding](#14-check-your-understanding)

---

## 1. Why use version control?

Imagine your group is preparing an event proposal. Without a system for tracking changes, you might end up with files such as:

```text
event-plan.md
event-plan-updated.md
event-plan-final.md
event-plan-final-v2.md
event-plan-really-final.md
```

You may then struggle to answer:

- Which version should we use?
- Who changed the budget?
- Why was an activity removed?
- How do we combine two members’ work?
- Can we inspect an earlier version?

Version control records changes to files over time so that you can inspect earlier versions and understand how a project developed. Git is a distributed version control system: a normal clone gives you a local repository with the project’s history, rather than only the latest files.

### How this helps your group

Instead of creating another “final” file, you record a change with a message:

```text
Add estimated activity durations
Revise budget for 120 students
Update venue arrangements for wet weather
```

The files remain part of one project, while the history records how they changed.

---

## 2. Git and GitHub are different

In this practical, Git manages the version history on your computer. GitHub provides the shared online repository and the pull request interface used for proposing, discussing and reviewing changes.

A pull request is not the same thing as a local Git commit or merge.

| Git | GitHub |
| --- | --- |
| Records project history locally. | Hosts the shared online repository. |
| Provides commands such as `add`, `commit` and `merge`. | Provides pull requests and review discussions. |
| Lets you inspect and record local changes. | Lets the group review and integrate shared contributions. |

### Example

You can edit `programme.md` and commit it locally without opening GitHub.

To share that commit, you push it to the remote repository.

To propose including the change in the group’s agreed version, you create a pull request.

These are separate actions.

---

## 3. Understanding a repository

A repository contains the project files together with the information Git uses to record their history.

For the Campus Connect project, the visible files might look like this:

```text
campus-connect/
├── README.md
├── event.md
├── team.md
├── overview.md
├── programme.md
├── publicity.md
└── logistics.md
```

Git also keeps its repository data in a `.git` directory. The files you currently see and edit form the working tree, also called the working directory.

### What does cloning do?

Cloning creates a local repository from an existing repository. For a normal clone, this includes the files and their history—not just a downloaded document folder.

```bash
git clone https://github.com/OWNER/campus-connect.git
```

Replace `OWNER` with the actual repository owner, or use the clone address provided by your instructor.

In the practical, every member clones the same shared repository.

```text
                    Shared repository
                        on GitHub
                            |
             +--------------+--------------+
             |              |              |
         Member 1       Member 2       Member 3
         local copy     local copy     local copy
```

Each local copy is separate. A change on one computer does not immediately appear on the others.

---

## 4. The working directory, staging area and commits

Git’s basic workflow has three important parts:

```text
Working directory → Staging area → Local repository
       edit             add             commit
```

You edit files in the working directory, select changes for the staging area and then record the staged snapshot as a commit. Git describes these states as modified, staged and committed.

### 4.1 Working directory: your current edits

Suppose you change this:

```text
Expected attendance: 80 students.
```

to:

```text
Expected attendance: 120 students.
```

After saving, the file contains your edit. However, you have not yet recorded it as a commit.

Inspect the change to this tracked file:

```bash
git diff
```

### 4.2 Staging area: your selection for the next commit

Stage the file:

```bash
git add logistics.md
```

Then inspect what you selected:

```bash
git diff --staged
```

The staging area allows you to decide what belongs in the next recorded change, rather than committing every edit in your folder together.

> [!NOTE]
> New, untracked files do not appear in ordinary `git diff` output. Stage a new file first, then inspect it with `git diff --staged`.

### 4.3 Commit: a recorded snapshot

Record the staged changes:

```bash
git commit -m "Update logistics for 120 students"
```

Git treats project history as a series of snapshots. A commit records the staged state, not simply whatever happens to be visible in your editor at the time.

### An important detail

Consider this sequence:

1. Edit `programme.md`.
2. Stage it.
3. Edit it again.
4. Commit without staging it again.

The commit contains the version selected at Step 2. The later edit remains outside that commit because staging selects the file’s content at the time you run `git add`.

Before committing, inspect:

```bash
git status
git diff --staged
```

### Writing useful commit messages

For this practical, use messages that explain the change:

| Less useful | More useful |
| --- | --- |
| `Update` | `Add registration details to publicity plan` |
| `Changes` | `Revise budget for 120 attendees` |
| `Fix stuff` | `Correct activity durations in programme` |

A useful message helps your group understand the history without opening every file change.

---

## 5. Understanding branches

A branch represents a separate line of development. Technically, it is a movable reference to a commit; it is not a separate GitHub repository or another manually copied project folder. As you commit on that branch, its reference advances.

### Why use a branch?

Your group treats `main` as the agreed version.

You create a feature branch to prepare a proposal without immediately adding it to `main`.

```text
A──B       main
    \
     C──D  feature/programme
```

In this example:

- `A` and `B` are shared earlier commits.
- `C` and `D` are new commits on `feature/programme`.
- `main` has not yet received those new commits.

### Creating and switching branches

```bash
git switch -c feature/programme
```

Check your current branch:

```bash
git branch --show-current
```

The branch determines where your next commit will be recorded. This is why the practical asks you to check your branch before editing and committing.

### Branches are not permanent personal ownership

A branch is usually named after a task:

```text
feature/programme
feature/publicity
update/rain-contingency
```

In the practical, these names help the group understand what each branch is meant to achieve.

---

## 6. Local and remote repositories

Your local repository and the shared remote repository do not update automatically whenever either one changes.

Git uses remote connections to exchange commits. A remote name such as `origin` is a convenient name for a repository address.

### Three names to distinguish

| Name | Meaning |
| --- | --- |
| `main` | Your local branch. |
| `origin` | A configured remote name. |
| `origin/main` | Your local record of the remote’s `main` branch. |

Remote-tracking references such as `origin/main` act as bookmarks showing the remote state Git last obtained. Fetching refreshes these references; they are not a continuously live view of GitHub.

### Example

Another member merges a PR on GitHub.

At that moment:

- GitHub’s `main` has changed.
- Your local `main` has not necessarily changed.
- Your `origin/main` may still reflect an earlier state until you fetch.

This distinction explains why your group needs to synchronise regularly.

---

## 7. Push, fetch and pull

These operations move information between repositories, but they do different jobs.

### 7.1 Push: publish your commits

```bash
git push -u origin feature/programme
```

This sends your local branch’s commits to the remote branch. Publishing a branch does not itself merge that branch into `main`.

The `-u` option sets the upstream relationship. After that, subsequent pushes from this branch can normally use `git push`.

```text
Local feature branch → Remote feature branch
```

### 7.2 Fetch: download updates without integrating them

```bash
git fetch origin
```

Fetch downloads remote data and updates remote-tracking references such as `origin/main`. It does not, by itself, merge those changes into your current branch.

```text
Remote updates → Local repository information
```

You can then decide which changes to integrate.

### 7.3 Pull: fetch and integrate

Pull combines downloading updates with integrating them into the current branch. Git supports different integration approaches; the practical uses a restricted fast-forward update for local `main`.

```bash
git switch main
git pull --ff-only origin main
```

The `--ff-only` option refuses the update if the branches have diverged and cannot be brought together by moving the local branch forward directly. If this happens, stop and ask your instructor for help rather than forcing the update.

The practical separates this from updating a feature branch:

```bash
git fetch origin
git merge origin/main --no-edit
```

Run that merge while on the feature branch that should receive the shared changes.

### Why does this matter?

| Intention | Practical workflow |
| --- | --- |
| Publish your feature work | Push your feature branch. |
| Obtain remote updates without integrating them | Fetch. |
| Update local `main` | Switch to `main`, then pull with `--ff-only`. |
| Bring shared work into your feature branch | Fetch, then merge `origin/main` while on the feature branch. |

---

## 8. Understanding merges

A merge combines another branch’s history with your current branch. Git may move the current branch forward directly, or create a merge commit when histories have diverged.

### Merge direction matters

Suppose your current branch is:

```text
feature/programme
```

You run:

```bash
git merge origin/main --no-edit
```

The direction is:

```text
origin/main → feature/programme
```

Your feature branch receives the shared work.

This does not put your feature work into `main`.

The `--no-edit` option accepts Git’s generated merge message if a merge commit is needed.

### Why update a feature branch?

While you are preparing the programme, another member may revise the venue.

Bringing the latest `main` into your feature branch lets you check your ongoing work against the accepted venue arrangements before the group integrates your proposal.

### An automatic merge is not a content review

Git may successfully combine changes without reporting a conflict. That only means it could perform the integration—not that the event proposal is consistent.

For example:

- One document says 120 attendees.
- Another document still budgets for 80.
- The files may merge without a technical conflict.

Your group must still review the meaning of the combined documents.

---

## 9. Understanding pull requests

A pull request proposes merging changes from one branch into another. It provides a place to discuss and review those changes before integration.

### Base and compare

```text
base: main
compare: feature/programme
```

Read this as:

> Propose bringing the changes from `feature/programme` into `main`.

| Field | Role |
| --- | --- |
| Base | Destination branch. |
| Compare | Branch containing the proposed changes. |

### What should reviewers inspect?

In the practical, reviewers should consider:

- Is the proposed content clear?
- Does it meet the task requirements?
- Are assumptions explained?
- Does it agree with other planning documents?
- Could the change remove useful information?
- What needs improvement before merging?

### Responding to feedback

You normally continue working on the PR’s existing source branch. After committing and pushing the improvement, the PR includes the updated branch changes.

You do not need a new PR for every response to review.

### A pull request is not the same as `git pull`

| Term | Meaning |
| --- | --- |
| `git pull` | Download and integrate remote changes locally. |
| Pull request | Propose and review branch integration on GitHub. |

---

## 10. Understanding merge conflicts

A merge conflict occurs when Git cannot automatically reconcile competing changes. A common example is two branches editing the same part of a file differently.

### Example

Original content:

```text
Venue: Seminar Room.
```

Your branch changes it to:

```text
Venue: Auditorium.
```

Another branch changes it to:

```text
Venue: Indoor Sports Hall.
```

Git may need a person to decide which venue is intended.

### Conflict markers

During the practical’s merge direction, you may see:

```text
<<<<<<< HEAD
Venue: Auditorium.
=======
Venue: Indoor Sports Hall.
>>>>>>> origin/main
```

| Marker | Meaning in this merge |
| --- | --- |
| `<<<<<<< HEAD` | Start of your current branch’s version. |
| `=======` | Divider between the versions. |
| `>>>>>>> origin/main` | End of the incoming version. |

The labels depend on which branch is current and which branch is being merged.

### Resolution is a decision, not just deletion

A correct resolution might retain one proposal or combine useful information:

```text
Venue: Auditorium.
Wet-weather holding area: Indoor Sports Hall.
```

However, that is only suitable if it matches the group’s actual decision. Do not invent a combined arrangement just to keep both lines.

After agreeing on the content, remove the markers, save the file, stage the resolution and complete the merge.

### Questions to discuss

- What was each member trying to achieve?
- Which information has already been accepted?
- Would choosing one side remove something important?
- Does the final version make sense across all documents?

A technically completed merge can still contain an incorrect decision.

---

## 11. Reading your repository state

When you are unsure what has happened, start with:

```bash
git status
```

Use it with `git diff` and `git diff --staged` to understand the working directory and the next proposed snapshot.

### Useful questions

| Question | Command |
| --- | --- |
| Which branch am I on? | `git branch --show-current` |
| What is the current file state? | `git status` |
| What tracked changes are not staged? | `git diff` |
| What is selected for the next commit? | `git diff --staged` |
| What commits are in the history? | `git log --oneline` |
| What does a particular commit contain? | `git show COMMIT_ID` |

Replace `COMMIT_ID` with an actual commit ID from your repository. Press `q` if you need to exit a scrolling history or diff viewer.

### Clean does not mean shared

A clean working directory means there are no outstanding file changes reported by Git. It does not, by itself, prove that your local commits have been pushed.

```text
Committed locally ≠ Published remotely
```

### Read messages before trying another command

For this practical:

1. Read the message.
2. Check your branch.
3. Inspect your working state.
4. Explain what you intended to do.
5. Ask for help if the next action could remove work.

Do not respond to every problem by pulling again or deleting files.

---

## 12. Putting the workflow together

Consider Member 2 preparing `programme.md`.

### Stage 1 — Obtain the project

Clone the shared repository.

You now have a local copy of its files and history.

### Stage 2 — Create a branch

Create `feature/programme`.

Your proposed work can now develop separately from the agreed `main`.

### Stage 3 — Record a focused change

Edit and save the document, inspect it, stage the intended content and commit it.

### Stage 4 — Share the work

Push the feature branch.

The commits are now available on GitHub.

### Stage 5 — Request review

Create a PR into `main`.

Another member inspects the proposal and gives feedback.

### Stage 6 — Improve the proposal

Make the improvement on the same branch, commit and push.

The reviewer checks the updated proposal.

### Stage 7 — Integrate shared changes

If `main` has advanced, bring its changes into your feature branch using the practical’s fetch-and-merge workflow.

Resolve any conflict and check the combined result.

### Stage 8 — Merge and synchronise

After review, merge the PR on GitHub.

Every member then updates their local `main`. A GitHub merge changes the shared repository, while local copies need a separate update.

```text
Clone
  ↓
Update main
  ↓
Create a branch
  ↓
Edit → Inspect → Stage → Commit
  ↓
Push
  ↓
Create PR → Review → Improve
  ↓
Integrate shared changes if needed
  ↓
Merge PR
  ↓
Update local main
```

---

## 13. Common misunderstandings

| Misunderstanding | More accurate understanding |
| --- | --- |
| “I saved the file, so Git has recorded it.” | Saving and committing are separate. |
| “I committed, so everyone can see it.” | You still need to publish the commits. |
| “I pushed, so my work is in `main`.” | A feature branch push does not merge it into `main`. |
| “Fetching updates my current files.” | Fetch downloads information; integration is separate. |
| “`origin/main` is always the latest GitHub version.” | It reflects the remote state most recently obtained. |
| “A branch is another copied project folder.” | A branch is a reference used to manage a line of development. |
| “A successful merge means the proposal is correct.” | The combined content still needs review. |
| “A conflict means someone has broken Git.” | A conflict means Git needs a human decision. |
| “My working directory is clean, so everything is shared.” | Local commits may still be unpublished. |

---

## 14. Check your understanding

Try answering these questions without running any commands.

### Scenario A — Saved but not recorded

You edited and saved `budget.md`, but have not staged or committed it.

1. Has Git recorded a new commit?
2. Has GitHub received the edit?
3. What should you inspect before committing?

### Scenario B — Recorded but not published

You committed your programme changes and closed the terminal without pushing.

1. Where is the commit?
2. Can your teammates obtain it from GitHub yet?
3. What action is still needed?

### Scenario C — Shared work has advanced

A teammate merged their PR into `main`.

1. Has your local `main` updated automatically?
2. What does fetching update?
3. Which workflow in the practical updates your local `main`?

### Scenario D — Merge direction

You are on `feature/publicity` and run:

```bash
git merge origin/main --no-edit
```

1. Which branch receives the changes?
2. Has your publicity work been merged into remote `main`?
3. What still needs to happen before it becomes part of the agreed proposal?

### Scenario E — Conflicting decisions

One branch changes the venue to the auditorium. Another changes it to the indoor sports hall.

1. Why should you discuss the intended result?
2. Why might keeping both proposals be incorrect?
3. What must you check after resolving the conflict?

---

## Closing reminder

Before asking, “Which command should I run?”, ask:

- Where am I working?
- Which branch am I on?
- What has changed?
- What is staged?
- What is committed?
- What has been shared?
- Which branch should receive the next change?

Once you understand these relationships, the commands become easier to use with confidence.
