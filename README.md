# Git and GitHub Team Practical

> A guided, hands-on introduction to version control and group collaboration for students with no prior Git experience.

> [!NOTE]
> ## Educational Practice Repository
>
> This public repository has been created solely for an introductory Git and GitHub collaboration practical. Its purpose is to help students practise version control, branching, pull requests, code review, merging and conflict resolution.
>
> All event plans, names, roles, dates, venues, budgets, organisations and other content included in this repository are fictional and prepared for educational purposes only. Any resemblance to actual persons, organisations, events or circumstances is purely coincidental.
>
> Do not include confidential, personal, sensitive, commercially sensitive or copyrighted material in this repository. This includes passwords, access tokens, API keys, identification numbers, personal contact details and private photographs.

This in-class practical helps you learn Git and GitHub by using them. You will work in a small group to prepare a simple fictional event proposal for **Campus Connect**.

The focus is on understanding the workflow through practice: creating branches, recording changes, sharing work, reviewing contributions, merging changes and resolving conflicts.

No programming experience is required. You will work with Markdown files: plain-text documents that use simple symbols for headings, lists and tables.

| Item | Details |
| --- | --- |
| Group size | 4–5 students |
| Guided in-class duration | Approximately 2.5 hours |
| Required tools | Git, GitHub, a terminal and a text editor |
| Practical outcome | A shared fictional event proposal and hands-on evidence of Git collaboration |
| Focus | Learning and practising Git workflows, not producing a polished event proposal |

## Contents

1. [Learning outcomes](#1-learning-outcomes)
2. [Understand the workflow](#2-understand-the-workflow)
3. [Prepare your group and computers](#3-prepare-your-group-and-computers)
4. [Create and clone the repository](#4-create-and-clone-the-repository)
5. [Create the starting files](#5-create-the-starting-files)
6. [Prepare your individual contribution](#6-prepare-your-individual-contribution)
7. [Create a pull request and respond to feedback](#7-create-a-pull-request-and-respond-to-feedback)
8. [Combine the group contributions](#8-combine-the-group-contributions)
9. [Set up a merge conflict](#9-set-up-a-merge-conflict)
10. [Resolve the conflict](#10-resolve-the-conflict)
11. [Inspect your Git history](#11-inspect-your-git-history)
12. [Guided reflection and completion](#12-guided-reflection-and-completion)
13. [Troubleshooting and command reference](#13-troubleshooting-and-command-reference)
14. [Individual completion checklist](#14-individual-completion-checklist)
15. [Optional extension activities — outside the in-class practical](#15-optional-extension-activities--outside-the-in-class-practical)

***

## 1. Learning outcomes

By the end of this practical, you should be able to:

- Clone a shared repository.
- Create and switch branches.
- Stage and commit changes.
- Push and pull changes.
- Create and review pull requests.
- Merge changes between branches.
- Resolve merge conflicts.
- Use Git history to explain your contributions.
- Coordinate changes with your group.

### Working through this practical

1. Complete the activities in sequence.
2. Enter commands in the terminal, not in your document.
3. Replace example names, addresses and filenames with your own.
4. Read the explanation before running each set of commands.
5. Wait for all members at each group checkpoint.

Use Git Bash on Windows, or Terminal on macOS or Linux.

> [!IMPORTANT]
> Run Git commands from inside your cloned repository unless instructed otherwise. Before making changes, check your current branch and working directory.

***

## 2. Understand the workflow

### Git and GitHub

Git records changes to your project files.

GitHub hosts the shared repository online and provides collaboration tools, including pull requests and reviews.

Your group will have:

- One shared public repository on GitHub.
- One local repository on each member’s computer.

> [!WARNING]
> A public GitHub repository can be viewed by anyone on the internet. Never commit passwords, access tokens, API keys, personal contact details, confidential information, private images or copyrighted material.

### A simple mental model

Think of GitHub as the group’s shared online folder with a change history.

Think of your local repository as your own copy of that folder on your computer.

A branch is like making a separate line of work so that you can edit safely without changing the agreed group version in `main`.

### Key terms

| Term | Meaning |
| --- | --- |
| Repository | A project folder and its recorded change history. |
| Shared repository | The group’s repository on GitHub. It is also called the remote repository. |
| Local repository | Your own project folder and Git history on your computer. |
| Clone | Create a local copy of an existing shared repository. |
| Branch | A separate line of work within the repository. |
| `main` | The shared branch containing the group’s agreed version of the project. |
| Personal work branch | Your own branch for making changes safely. It is also called a feature branch. |
| Current branch | The branch you are currently working on. New changes and commits are made here. |
| Working directory | The project files on your computer that you can edit. |
| Staging area | A selection area where you choose changes for your next commit. It is not a separate folder. |
| Commit | A recorded snapshot of selected changes. |
| Push | Send your local commits to GitHub. |
| Fetch | Download information about updates on GitHub without changing your current files. |
| Pull | Download GitHub updates and integrate them into your current branch. |
| Merge | Combine changes from one branch into another branch. |
| Pull request, or PR | A request on GitHub to review and merge changes from one branch into another. |
| Merge conflict | Competing changes that require a person to decide the final content. |
| `origin` | The short name Git normally gives to the group’s shared GitHub repository after cloning. |
| `origin/main` | Your computer’s latest downloaded record of the `main` branch on GitHub. It is refreshed by `git fetch origin`. |
| Commit ID | A short code that identifies a commit, such as `a1b2c3d`. |

### Saving, committing and sharing

```text
Save   → Write changes to a file.
Commit → Record selected changes locally.
Push   → Send local commits to GitHub.
PR     → Propose merging one branch into another.
```

Saving a file does not create a commit. Committing does not upload your work. Pushing a personal work branch does not merge it into `main`.

### Group working rules

- Work on your own personal work branch, not directly on `main`.
- Keep commits focused and use clear commit messages.
- Ask another member to review each PR.
- Merge PRs one at a time.
- Start branch switches and merges with no uncommitted changes.
- Keep these practical instructions in `README.md`.
- Use fictional information only for the Campus Connect proposal.
- Do not add confidential, personal, sensitive, commercially sensitive or copyrighted content.

> [!WARNING]
> Do not force-push, use `git reset --hard` or delete the repository to get past an error. Preserve your work, inspect the situation and ask your Tutor if needed. Never include passwords or access tokens in project files.

***

## 3. Prepare your group and computers

### 3.1 Assign responsibilities

| Member | Initial responsibility | File | Reviewer |
| --- | --- | --- | --- |
| 1 | Overview and initial coordination | `overview.md` | Member 5, or Member 4 for a group of four |
| 2 | Programme | `programme.md` | Member 1 |
| 3 | Publicity | `publicity.md` | Member 2 |
| 4 | Logistics | `logistics.md` | Member 3 |
| 5, if any | Budget | `budget.md` | Member 4 |

For a group of four, include the budget in `logistics.md`.

These are starting responsibilities. You will also review and improve documents prepared by other members.

Each member must use their own computer and GitHub account.

### 3.2 Check that Git is installed

Open your terminal:

```bash
git --version
```

Expected result: a Git version number.

If the command is not recognised, ask your Tutor to check your installation.

### 3.3 Set your commit identity

Replace the example values:

```bash
git config --global user.name "Your Name"
git config --global user.email "YOUR_COMMIT_EMAIL"
```

Check your settings:

```bash
git config --global user.name
git config --global user.email
```

Use an email associated with your GitHub account, or your GitHub-provided no-reply email.

These settings identify the author of future commits. They do not sign you in to GitHub.

Complete the authentication setup needed to push changes before continuing.

### Checkpoint

- [ ] Everyone has Git, a text editor and a GitHub account.
- [ ] Everyone has completed authentication setup.
- [ ] Everyone knows their member number, responsibility and reviewer.
- [ ] Everyone understands that only fictional, non-sensitive information may be committed.

***

## 4. Create and clone the repository

### 4.1 Coordinator only: create the shared repository

On GitHub:

1. Create a repository named `campus-connect`.
2. Set the repository visibility to **Public**.
3. Add a README when creating the repository.
4. Confirm that the default branch is `main`.
5. Place these instructions in `README.md`, including the **Educational Practice Repository** disclaimer at the top.
6. Invite your group members through the collaborator settings.
7. Add your class Tutor as a repository collaborator using the GitHub username provided by your Tutor.
8. Confirm that all group members and the Tutor have accepted their invitations.

> [!IMPORTANT]
> This repository must be public. Public repositories are accessible to anyone on the internet, so only fictional and non-sensitive content may be included.

> [!NOTE]
> To add group members or your Tutor as collaborators, open the repository’s **Settings**, select **Collaborators** under **Access**, choose **Add people**, then search for the person’s GitHub username and send the invitation.

> [!NOTE]
> If your Tutor has provided a shared repository, use it instead. Only one shared repository is needed for the group. Confirm that it is public and that the Tutor has collaborator access.

### 4.2 Everyone: clone the repository

On GitHub:

1. Open your group’s `campus-connect` repository.
2. Select **Code**.
3. Select **HTTPS**.
4. Select the copy icon to copy the repository URL.

Open Git Bash or Terminal in the folder where you normally keep projects.

Type `git clone`, add one space, then paste the HTTPS URL that you copied from GitHub:

```bash
git clone PASTE_THE_HTTPS_URL_COPIED_FROM_GITHUB_HERE
```

For example, after pasting your group’s actual URL, the command will look similar to this:

```bash
git clone [https://github.com/your-group-owner/campus-connect.git](https://github.com/your-group-owner/campus-connect.git)
```

Press **Enter**. Git creates a new folder named `campus-connect`.

Enter the new project folder:

```bash
cd campus-connect
```

> [!IMPORTANT]
> Do not type `PASTE_THE_HTTPS_URL_COPIED_FROM_GITHUB_HERE` literally. Replace it by pasting the HTTPS URL copied from your group’s GitHub repository.

Cloning creates a new folder, downloads the project files and their history, and normally sets up a remote named `origin`.

### 4.3 Inspect your local repository

Do not worry if the command output contains unfamiliar information. At this stage, focus only on the checks shown in the table.

```bash
git status
git branch
git remote -v
git log --oneline -5
```

| Command | What to check |
| --- | --- |
| `git status` | Your current branch and any uncommitted changes. |
| `git branch` | Your local branches. The `*` indicates your current branch. |
| `git remote -v` | Check that `origin` is the short name for your group’s GitHub repository and that the displayed address belongs to your group. |
| `git log --oneline -5` | Up to five recent commits, shown as short lines. |

If the output opens in a scrolling view, press `q` to exit.

### Checkpoint

- [ ] The repository visibility is **Public**.
- [ ] Group members have been invited and have accepted access.
- [ ] The class Tutor has been invited as a collaborator using the GitHub ID provided.
- [ ] The educational-practice disclaimer is visible in `README.md`.
- [ ] I am inside the cloned repository.
- [ ] My current branch is `main`.
- [ ] My working directory is clean.
- [ ] `origin` points to our shared repository.

Discuss with another member:

1. Where is your local repository?
2. Where is the shared repository?
3. Does cloning create another repository on GitHub?

***

## 5. Create the starting files

> [!IMPORTANT]
> The coordinator completes this section first. Other members wait until the setup PR has been merged.

### 5.1 Create a setup branch

```bash
git switch main
git pull --ff-only origin main
git switch -c setup/event-files
```

| Command | Purpose |
| --- | --- |
| `git switch main` | Select your local `main` branch. |
| `git pull --ff-only origin main` | Safely update local `main` from GitHub. Git stops instead of combining histories if it finds unexpected local commits. |
| `git switch -c setup/event-files` | Create and switch to the setup branch. |

The `--ff-only` option stops the update if Git cannot move the local branch directly forward to match GitHub without combining different histories. If it refuses, use the troubleshooting steps in Section 13 to inspect and preserve your work before asking your Tutor for help.

The `/` in the branch name is a naming convention, not a folder.

### 5.2 Create `event.md`

Create this file in the repository’s top-level folder:

```markdown
# Campus Connect

Event date: To be confirmed.
Venue: To be confirmed.
Organisers: To be confirmed.

## Purpose

Bring students together through a welcoming campus event.

## Planning documents

The group will add its planning documents during the practical.
```

Save the file.

> [!IMPORTANT]
> Keep `Organisers: To be confirmed.` exactly as shown. It is needed for the conflict-resolution activity.

### 5.3 Create `team.md`

```markdown
# Team

| Member | Name | GitHub username | Responsibility |
| --- | --- | --- | --- |
| 1 | Name | Username | Overview |
| 2 | Name | Username | Programme |
| 3 | Name | Username | Publicity |
| 4 | Name | Username | Logistics |
```

Replace the examples with your group’s details. Add Member 5 if needed.

> [!NOTE]
> Use first names or agreed non-sensitive identifiers only. Do not include personal email addresses, phone numbers, student numbers or other private details in this public repository.

### 5.4 Stage, commit and push

```bash
git status
git add event.md team.md
git diff --staged
git commit -m "Add initial event plan and team details"
git status
git push -u origin setup/event-files
```

Explanation:

- `git add` places selected file changes into the staging area: the changes you want included in your next commit.
- `git diff --staged` shows exactly what will be included in the next commit.
- `git commit` records the staged changes in your local repository.
- `git push` sends your local commits to GitHub.
- `-u` remembers the matching branch on GitHub, so later you can usually run `git push` without typing the branch name again.

### 5.5 Create and merge the setup PR

On GitHub:

1. Open **Pull requests**.
2. Create a new PR.
3. Set the base branch to `main`.
4. Set the compare branch to `setup/event-files`.
5. Give the PR a clear title.
6. Inspect **Files changed**.
7. Ask another member to review.
8. Merge after review.

Remember:

- **Base** is the destination branch that receives the changes: `main`.
- **Compare** is the branch containing the proposed changes: `setup/event-files`.

The base branch receives the changes when the PR is merged. The compare branch contains the proposal.

Select **Create a merge commit** if available.

### 5.6 Everyone: update local `main`

```bash
git switch main
git pull --ff-only origin main
git status
```

Confirm that `event.md` and `team.md` are present locally.

The coordinator must also do this. Merging on GitHub does not automatically update anyone’s computer.

### Checkpoint

- [ ] The setup PR has been reviewed and merged.
- [ ] Everyone has updated local `main`.
- [ ] Everyone can open `event.md` and `team.md`.

***

## 6. Prepare your individual contribution

### 6.1 Create your personal work branch

After updating `main`, run only your assigned command:

| Member | Command |
| --- | --- |
| 1 | `git switch -c feature/overview` |
| 2 | `git switch -c feature/programme` |
| 3 | `git switch -c feature/publicity` |
| 4 | `git switch -c feature/logistics` |
| 5 | `git switch -c feature/budget` |

Check:

```bash
git branch --show-current
git status
```

Make sure you are on your personal work branch, not `main`.

### 6.2 Create your document

Use your assigned filename. Include:

- A suitable heading.
- At least two sections.
- At least five useful planning points.
- One assumption or question for group discussion.

Example:

```markdown
# Programme

## Proposed activities

- Welcome and registration.
- Group icebreaker.
- Campus discovery challenge.
- Sharing session.
- Closing and feedback.

## Questions for discussion

- How much time is available?
- How many students are expected?
```

Prepare your own fictional content. Do not edit `event.md` yet.

### 6.3 Commit and push

The example below is for Member 2. Use your own filename, branch and commit message.

```bash
git status
git add programme.md
git diff --staged
git commit -m "Add programme and questions for discussion"
git status
git log --oneline -3
git push -u origin feature/programme
```

> [!TIP]
> A new file is initially untracked. This means Git has noticed the file but is not yet tracking it for commits. A new untracked file does not appear in ordinary `git diff` output. Stage it first, then inspect it with `git diff --staged`.

### Checkpoint

- [ ] My document has been committed.
- [ ] My working directory is clean.
- [ ] My branch is available on GitHub.
- [ ] My document contains fictional, non-sensitive information only.

***

## 7. Create a pull request and respond to feedback

### 7.1 Create your PR

Use these branch settings:

```text
base: main
compare: your personal work branch
```

Remember:

- **Base** is the destination branch that will receive the changes: `main`.
- **Compare** is your personal work branch containing the proposed changes.

Give the PR a clear title and use this description template:

```markdown
## What changed?

Describe the document or sections added.

## Why is this needed?

Explain how this helps the event plan.

## What should the reviewer check?

Identify details or assumptions that need attention.

## Questions for discussion

List decisions that the group still needs to make.
```

### 7.2 Review another member’s work

Read the PR description and **Files changed**.

Provide:

- One useful question or suggestion.
- One comment on something clear or helpful.

Example:

> The activity sequence is clear. Could you add the estimated duration for each activity so we can check whether the programme fits within the available time?

Do not approve without inspecting the changes.

### 7.3 Respond to the review

Make the improvement on the same personal work branch. Save the file, then run:

```bash
git diff
git add programme.md
git diff --staged
git commit -m "Add activity durations following review"
git push
```

Use your actual filename and a suitable message.

The existing PR updates when you push commits to its source branch. Do not create another PR for this response.

The reviewer checks the update and approves when ready.

> [!IMPORTANT]
> Do not merge the individual PRs yet. Integration starts in the next section.

### Checkpoint

- [ ] Everyone has created a PR.
- [ ] Everyone has reviewed another member’s work.
- [ ] Everyone has made an improvement following review.
- [ ] All PRs are ready for integration.

***

## 8. Combine the group contributions

### 8.1 Merge Member 1’s PR first

After review, another member merges Member 1’s PR on GitHub.

Everyone waits until this is complete.

### 8.2 Member 2: update your personal work branch

Stay on your personal work branch. Start with no uncommitted changes.

```bash
git status
git fetch origin
git merge origin/main --no-edit
git status
git log --oneline --graph --all -12
git push
```

Explanation:

- `git fetch origin` downloads information about the latest GitHub changes but does not change your files.
- `origin/main` means the latest version of the shared `main` branch that Git knows about after fetching.
- `git merge origin/main --no-edit` brings those shared changes into your current personal work branch.
- `--no-edit` accepts Git’s automatic merge-commit message if Git needs to create one.

You are updating your own work branch with changes already accepted into `main`. You are not yet putting your work branch into `main`.

```text
Changes are moving in this direction:

shared main on GitHub → your personal work branch
```

The initial contributions use separate files, so they should combine without a conflict.

The reviewer checks the updated PR and merges it.

### 8.3 Continue in member-number order

Members 3, 4 and 5 take turns:

1. Wait for the previous PR to be merged.
2. Fetch the latest changes from GitHub.
3. Merge `origin/main` into your personal work branch.
4. Inspect the result and push.
5. Obtain review and merge the PR.

Member 1 will practise command-line merging during the conflict activity.

### 8.4 Everyone: update local `main`

```bash
git switch main
git pull --ff-only origin main
git status
```

### Checkpoint

- [ ] All contribution PRs have been merged.
- [ ] Everyone has all planning documents locally.
- [ ] Everyone’s working directory is clean.

### Discussion

Explain to another member:

1. What did `fetch` do?
2. What did `merge` do?
3. Why did everyone still need to pull after the GitHub merges?

***

## 9. Set up a merge conflict

Each member must resolve a conflict personally.

### 9.1 Start from the same version

Everyone runs:

```bash
git switch main
git pull --ff-only origin main
git status
```

Confirm that `event.md` still contains:

```text
Organisers: To be confirmed.
```

> [!IMPORTANT]
> Wait until everyone reaches this point. Do not merge any other changes yet.

### 9.2 Create your conflict branch

Use your own member number:

```bash
git switch -c conflict/member-1
```

Other members use `conflict/member-2`, `conflict/member-3` and so on.

Replace the organiser line with your own entry.

Member 1 writes:

```text
Organisers: Member 1.
```

Member 2 writes:

```text
Organisers: Member 2.
```

Save, commit and push using your actual branch name:

```bash
git add event.md
git commit -m "Propose organiser entry for my member number"
git push -u origin conflict/member-1
```

Create a PR into `main`. Do not merge it.

### Group checkpoint — wait here

- [ ] Everyone has created a conflict branch.
- [ ] Everyone has committed a different replacement for the same line.
- [ ] Everyone has pushed and created a PR.
- [ ] None of these PRs has been merged.

The coordinator continues only after all members reach this checkpoint.

### 9.3 Coordinator: update the shared version

You have already committed your own organiser-line change on your conflict branch. Create a separate branch:

```bash
git switch main
git pull --ff-only origin main
git switch -c setup/coordinator-entry
```

Change the organiser line to:

```text
Organisers: Team coordinator.
```

Then run:

```bash
git add event.md
git commit -m "Add coordinator to organiser entry"
git push -u origin setup/coordinator-entry
```

Create a PR, obtain review and merge it.

Do not merge the personal conflict PRs yet.

***

## 10. Resolve the conflict

> [!IMPORTANT]
> Proceed in member-number order. Each member waits until the previous member’s resolved PR has been reviewed and merged.

### 10.1 Bring the latest shared version into your conflict branch

Use your own branch name:

```bash
git switch conflict/member-1
git status
git fetch origin
git merge origin/main --no-edit
```

Start only with no uncommitted changes.

Git should report a conflict in `event.md` and pause the merge.

Do not pull again or start another merge.

Inspect the state:

```bash
git status
```

Git should identify `event.md` as an unmerged file.

### 10.2 Read the conflict markers

Git is asking you to choose the final version because your branch and `main` changed the same line differently. The markers are temporary notes inserted by Git; they must not remain in the finished file.

Member 1 should see something similar to:

```text
<<<<<<< HEAD
Organisers: Member 1.
=======
Organisers: Team coordinator.
>>>>>>> origin/main
```

| Marker | Meaning in this merge |
| --- | --- |
| `<<<<<<< HEAD` | Start of the version currently on your conflict branch. |
| `=======` | Divider between the two versions. |
| `>>>>>>> origin/main` | End of the version coming from the shared `main` branch. |

### 10.3 Decide the final content

Keep everyone already listed on `main`, then add yourself.

Member 1 resolves the line to:

```text
Organisers: Team coordinator, Member 1.
```

After that PR is merged, Member 2 resolves the line to:

```text
Organisers: Team coordinator, Member 1, Member 2.
```

Continue until all members are included.

Remove every conflict marker and inspect the whole file.

Do not keep only your version if it removes another member’s accepted contribution.

### 10.4 Complete the merge

Save the file, then run:

```bash
git diff
git add event.md
git diff --staged
git diff --staged --check
git status
git commit -m "Resolve organiser conflict and retain agreed entries"
git status
git push
```

Explanation:

- Staging marks the file as resolved.
- Committing completes the merge.
- Pushing updates the existing PR.

The `--check` option can identify remaining conflict markers and whitespace issues. It cannot determine whether the final content is correct.

### 10.5 Review and merge

The reviewer verifies that:

- All conflict markers have been removed.
- Previously accepted organisers remain listed.
- The current member has been added.
- No unrelated content has been removed.

Merge the PR. Only then should the next member start Section 10.1.

### Cancelling an in-progress merge

If you need to cancel a merge that is still in progress:

```bash
git merge --abort
```

Resolution edits may be discarded. Ask your Tutor if you are unsure.

### Final conflict checkpoint

After everyone has completed the activity:

```bash
git switch main
git pull --ff-only origin main
git status
```

- [ ] The organiser line includes everyone.
- [ ] Every member personally resolved a conflict.
- [ ] Everyone’s local `main` is updated.
- [ ] Everyone’s working directory is clean.

***

## 11. Inspect your Git history

Run:

```bash
git log --oneline --graph --decorate --all -25
```

| Option | Purpose |
| --- | --- |
| `--oneline` | Show one short line for each commit. |
| `--graph` | Draw a simple text diagram showing where branches and merges happened. |
| `--decorate` | Show branch names beside relevant commits. |
| `--all` | Include commits from all local branches. |
| `-25` | Show at most 25 commits. |

Find:

1. One of your content commits.
2. A commit made by another member.
3. A merge commit.
4. Your conflict-resolution commit.

Inspect a commit using its actual ID:

```bash
git show COMMIT_ID
```

Replace `COMMIT_ID` with a short commit ID from your repository, such as `a1b2c3d`.

Explain to another member:

- What changed in the commit?
- How do you know?
- What decision did your conflict-resolution commit record?

***

## 12. Guided reflection and completion

Create `retrospective.md` through a reviewed pull request.

Keep your reflection short and specific:

- One Git task you can now complete independently.
- One useful review comment you gave or received.
- One improvement made after feedback.
- One conflict you resolved and how you decided the final content.
- One Git skill you would like to practise further.

### Final practical checklist

- [ ] Everyone created and used a personal work branch.
- [ ] Everyone created a commit and pushed work to GitHub.
- [ ] Everyone created a pull request.
- [ ] Everyone reviewed another member’s pull request.
- [ ] Everyone made an improvement after review feedback.
- [ ] Everyone personally resolved a merge conflict.
- [ ] The group’s `main` branch contains the agreed files.
- [ ] Everyone updated their local `main` branch.
- [ ] Everyone’s working directory is clean.
- [ ] No confidential or sensitive information is present.

***

## 13. Troubleshooting and command reference

### Before attempting a fix

1. Read the error message.
2. Run `git status`.
3. Check your current branch.
4. Confirm what you intended to do.
5. Preserve your work before making further changes.

### `git pull --ff-only` refuses

The command below updates local `main` only when Git can move it directly forward to match the latest version on GitHub:

```bash
git pull --ff-only origin main
```

A successful fast-forward update does not create a merge commit. Git moves your local `main` branch directly forward because it has no commits that are missing from the shared `main` branch on GitHub.

You may see this error:

```text
fatal: Not possible to fast-forward, aborting.
```

This means that your local `main` branch and `origin/main` have diverged. In other words:

- Your local `main` branch has one or more commits that are not on GitHub.
- GitHub has one or more commits that are not in your local `main` branch.
- Git refuses to combine the two histories automatically because `--ff-only` permits only a direct forward update.

This is a warning to stop and review the repository state. It helps prevent an unexpected merge commit on `main`.

#### Review the situation

Do not force-push, run `git reset --hard`, delete files or immediately try another pull command.

Run these commands:

```bash
git status
git branch --show-current
git fetch origin
git log --oneline --graph --decorate --all -15
```

Review the output:

| Check | What to look for |
| --- | --- |
| `git status` | Uncommitted changes or a merge already in progress. |
| `git branch --show-current` | Confirm whether you are on `main` or a personal work branch. |
| `git fetch origin` | Download the latest remote information without changing your files. |
| `git log --oneline --graph --decorate --all -15` | Identify commits that exist only on local `main` or only on `origin/main`. |

#### Decide what happened

| Situation | Likely cause | What to do |
| --- | --- | --- |
| You are on `main` and have committed your own work locally. | You accidentally committed directly on `main`. | Preserve the commit by creating a recovery branch. Do not reset or force-push. |
| You are on a personal work branch. | You used the `main` update command on the wrong branch. | Check the branch name. Use `git fetch origin`, then merge `origin/main` into your personal work branch when required by the activity. |
| The graph shows unfamiliar commits or you cannot explain the history. | A branch may have been merged locally, or the wrong branch may have been used. | Stop and ask your Tutor after recording the command output or taking a screenshot. |
| There are uncommitted changes. | Work has not yet been committed or safely stored. | Inspect the changes with `git diff` and preserve them before switching branches. |

#### Preserve accidental work on `main`

If you confirm that your own commits are on local `main`, create a recovery branch before taking any further action:

```bash
git switch -c recovery/my-main-work
```

This creates a new branch containing your current commits, so your work remains available even after you return to `main`.

Next, review the graph and ask your Tutor how the work should be moved into the appropriate personal work branch.

> [!IMPORTANT]
> Do not use `git pull --no-ff`, `git pull --rebase`, `git reset --hard` or `git push --force` to bypass the error during this practical unless your Tutor explicitly directs you to do so.

### Common problems

| Problem | What to check first |
| --- | --- |
| “Not a Git repository” | Check your location and enter the cloned project folder. |
| Local changes would be overwritten | Inspect `git status` and `git diff`. Preserve your work before continuing. |
| Changes missing on GitHub | Check saving, staging, committing, pushing and the branch displayed on GitHub. |
| Push rejected | Check access, authentication and whether the remote branch has newer commits. Do not force-push. |
| `pull --ff-only` refuses | Follow the `git pull --ff-only` troubleshooting section above. |
| Unexpected files in a PR | Check the base branch, compare branch and branch history. |
| Unresolved conflict | Inspect every unmerged file, agree final content, remove markers, stage and commit. |
| Sensitive information committed | Stop sharing the material, inform your Tutor immediately and follow your Tutor’s instructions. Do not assume that deleting the file removes it from Git history. |

### Remote personal work branch has newer commits

If someone has pushed commits to the same personal work branch, fetch and integrate that matching branch before pushing.

For example, while on `feature/programme`:

```bash
git fetch origin
git merge origin/feature/programme --no-edit
```

Resolve any conflict, complete the merge if needed, then push.

Use your actual branch name. This does not fix an authentication or permission error.

### Command reference

| Command | Purpose |
| --- | --- |
| `git clone PASTE_THE_HTTPS_URL_COPIED_FROM_GITHUB_HERE` | Create a local copy using the HTTPS URL copied from GitHub. |
| `git status` | Inspect your current branch and working state. |
| `git branch --show-current` | Show the name of your current branch. |
| `git switch main` | Switch to your local `main` branch. |
| `git switch -c feature/name` | Create and switch to a new personal work branch. |
| `git diff` | Inspect unstaged changes to tracked files. |
| `git add FILE` | Select a file’s changes for the next commit. |
| `git diff --staged` | Inspect changes selected for the next commit. |
| `git commit -m "Message"` | Record staged changes in your local repository. |
| `git push -u origin BRANCH` | Publish a branch on GitHub and remember it as the matching branch for later pushes. |
| `git push` | Send commits to the matching branch on GitHub. |
| `git fetch origin` | Download information about GitHub updates without changing your current files. |
| `git pull --ff-only origin main` | Safely update local `main` if Git can move it directly forward; use while on `main` in this practical. |
| `git merge origin/main --no-edit` | Bring the latest shared `main` changes into your current personal work branch. |
| `git merge --abort` | Cancel a merge that is still in progress. |
| `git log --oneline` | View a compact commit history. |
| `git show COMMIT_ID` | Inspect a particular commit. |

***

## 14. Individual completion checklist

- [ ] I cloned the shared repository.
- [ ] I created and switched to my own personal work branch.
- [ ] I inspected changes before committing.
- [ ] I staged and committed my own work.
- [ ] I pushed my branch to GitHub.
- [ ] I created a PR.
- [ ] I reviewed another member’s work.
- [ ] I responded to review feedback.
- [ ] I updated local `main` after a GitHub merge.
- [ ] I merged shared changes into a personal work branch.
- [ ] I personally resolved and committed a conflict.
- [ ] I can find and explain one of my commits.
- [ ] I confirmed that I did not commit confidential, personal or sensitive information.
- [ ] My local `main` is updated and my working directory is clean.

***

## 15. Optional extension activities — outside the in-class practical

The activities in this section are **not required** for the 2.5-hour guided in-class practical.

Students are encouraged to attempt them independently, outside class, if they have the interest, time and bandwidth. They provide additional hands-on practice with branches, pull requests, reviews, merging and conflict resolution.

Choose one or more activities after completing the required practical.

### A. Improve the handover

A new committee member has five minutes to understand the plan.

Improve navigation to:

- Event summary.
- Programme.
- Budget.
- Contingency arrangements.
- Outstanding decisions.
- Member responsible for each planning area.

Ask another group to find all six without your help.

### B. Review an incomplete proposal

Prepare a realistic but incomplete improvement, such as:

- A programme without transition time.
- A budget missing an expense.
- A publicity plan without registration details.

Submit it as a PR. The reviewer identifies the issue and its consequence. The author improves the proposal before merging.

### C. Coordinate overlapping work

Two members independently improve the same section with useful but different proposals.

Produce one consistent final version and explain:

- What each member intended.
- Where the proposals overlapped.
- What the group kept, changed or removed.
- Why the final version was suitable.

### D. Review another group’s repository

Exchange repository links.

Without a verbal explanation, identify:

- One strength.
- One inconsistency.
- One missing detail.
- One question affecting whether the event can be carried out.

Discuss which feedback to accept and implement the changes through reviewed PRs.

***

## Closing reminder

The aim is not to memorise every command. Develop the habit of understanding your current state, making focused changes, inspecting the result and sharing work carefully.

```text
Check → Update → Branch → Edit → Inspect → Commit
      → Push → Review → Improve → Merge → Synchronise
```
