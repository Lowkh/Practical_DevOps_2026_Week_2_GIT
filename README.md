````markdown
# Git and GitHub Team Practical

## Plan a Campus Event Together

In this practical, your group will prepare a plan for **Campus Connect** while learning to use Git and GitHub.

No programming experience is required. You will work with Markdown files, which are plain-text documents that use simple symbols for headings, lists and tables.

| Item | Details |
|---|---|
| Intended audience | Students with no prior Git experience |
| Group size | 4–5 students |
| Guided activities | Approximately 3–4 hours |
| Independent practice | Approximately 1–2 hours |
| Tools | Git, GitHub, a terminal and a text editor |

---

## 1. Learning Outcomes

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

### How to use this practical

1. Complete the activities in sequence.
2. Enter commands in the terminal, not in your document.
3. Replace example names, addresses and filenames with your own.
4. Read the explanation before running each set of commands.
5. At each group checkpoint, wait until all members are ready before continuing.

Use Git Bash on Windows, or Terminal on macOS or Linux.

Run Git commands from inside your cloned repository unless instructed otherwise.

Before making changes, check your current branch and working directory.

---

## 2. Understand the Workflow

### Git and GitHub

Git records changes to your project.

GitHub stores the shared repository online and provides tools for collaboration, such as pull requests and reviews.

Your group will have:

- One shared remote repository on GitHub.
- One local repository on each member’s computer.

### Key terms

| Term | Meaning |
|---|---|
| Repository | Your project files and their Git history. |
| Clone | Create a local copy of an existing repository. |
| Branch | A separate line of work within the repository. |
| `main` | The branch containing the group’s agreed version of the project. |
| Working directory | The project files currently available for you to edit. |
| Staging area | Changes selected for the next commit. |
| Commit | A recorded snapshot of selected changes. |
| Push | Send local commits to the remote repository. |
| Fetch | Download remote updates without combining them with your current branch. |
| Pull | Download updates and combine them with your current branch. |
| Merge | Combine another branch’s changes with your current branch. |
| Pull request, or PR | A proposal on GitHub to merge one branch into another. |
| Merge conflict | Competing changes that require someone to decide the final content. |
| `origin` | The remote name normally created when you clone a repository. |

### Saving, committing and sharing are different

```text
Save   → Write your changes to a file.
Commit → Record selected changes in your local repository.
Push   → Send local commits to GitHub.
PR     → Propose merging your branch into another branch.
```

Saving a file does not create a commit. Committing does not upload your work. Pushing a feature branch does not merge it into `main`.

### Group working rules

- Work on your own branch, not directly on `main`.
- Keep each commit focused and use a clear commit message.
- Ask another member to review your PR.
- Merge PRs one at a time.
- Make sure there are no uncommitted changes before switching branches or starting a merge.
- Do not force-push or use `git reset --hard`.
- Do not delete the repository just to get past an error.
- Do not include passwords or access tokens in project files.
- Keep these practical instructions in `README.md`.

---

## 3. Prepare Your Group and Computers

### Activity 3A — Assign member numbers and responsibilities

| Member | Initial responsibility | File | Reviewer |
|---|---|---|---|
| 1 | Overview and initial coordination | `overview.md` | Member 5, or Member 4 for a group of four |
| 2 | Programme | `programme.md` | Member 1 |
| 3 | Publicity | `publicity.md` | Member 2 |
| 4 | Logistics | `logistics.md` | Member 3 |
| 5, if any | Budget | `budget.md` | Member 4 |

For a group of four, include the budget in `logistics.md`.

These are your starting responsibilities. You will also review and improve documents prepared by other members.

Each member must use their own computer and GitHub account.

### Activity 3B — Check that Git is installed

Open your terminal and run:

```bash
git --version
```

You should see a Git version number.

If the command is not recognised, ask your lecturer or instructor to check your installation.

### Activity 3C — Set your commit identity

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

Use an email address associated with your GitHub account, or your GitHub-provided no-reply email address.

These settings identify the author of future commits. They do not sign you in to GitHub.

Complete the authentication setup needed to push changes before continuing.

### Group checkpoint

- [ ] Everyone has Git, a text editor and a GitHub account.
- [ ] Everyone has completed the authentication setup.
- [ ] Everyone knows their member number, responsibility and reviewer.

---

## 4. Create and Clone the Shared Repository

### Activity 4A — Coordinator only: create the repository

On GitHub:

1. Create a repository named `campus-connect`.
2. Select the visibility specified by your instructor.
3. Add a README when creating the repository.
4. Check that the default branch is `main`.
5. Place these practical instructions in `README.md` if they are not already provided.
6. Invite your group members through the repository’s collaborator settings.

Each member must accept the invitation.

If your instructor has already provided a shared repository, use that repository instead.

Only one shared repository is needed for the group.

### Activity 4B — Everyone: clone the repository

On GitHub:

1. Select Code.
2. Select HTTPS.
3. Copy the repository address.

Open the terminal in the folder where you normally keep your projects.

Run the following using your group’s actual repository address:

```bash
git clone [https://github.com/OWNER/campus-connect.git](https://github.com/OWNER/campus-connect.git)
cd campus-connect
```

Do not use `OWNER` unchanged.

Cloning creates the project folder, downloads its files and history, and normally sets up a remote called `origin`.

### Activity 4C — Check your local repository

```bash
git status
git branch
git remote -v
git log --oneline -5
```

| Command | What to check |
|---|---|
| `git status` | Your current branch and any uncommitted changes. |
| `git branch` | Your local branches. The `*` indicates the current branch. |
| `git remote -v` | The remote repository addresses. |
| `git log --oneline -5` | Up to five recent commits. |

If the output opens in a scrolling view, press `q` to exit.

### Individual checkpoint

- [ ] I am inside the cloned repository.
- [ ] My current branch is `main`.
- [ ] My working directory is clean.
- [ ] `origin` points to our shared repository.

Discuss with another member:

- Where is your local repository?
- Where is your remote repository?
- Does cloning create another repository on GitHub?

---

## 5. Create the Starting Files

The coordinator completes this section first. The other members wait until the setup PR has been merged.

### Activity 5A — Create a setup branch

```bash
git switch main
git pull --ff-only origin main
git switch -c setup/event-files
```

Explanation:

- `git switch main` selects your local `main` branch.
- `git pull --ff-only origin main` updates it from GitHub.
- `git switch -c` creates a new branch and switches to it.

The `--ff-only` option stops the update if Git cannot move the branch forward without combining different histories. If this happens, ask your instructor for help.

The `/` in the branch name is a naming convention. It does not create a folder.

### Activity 5B — Create `event.md`

Create the following file in the repository’s main folder:

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

Keep the `Organisers` line exactly as shown. You will use it for the conflict-resolution activity.

### Activity 5C — Create `team.md`

```markdown
# Team

| Member | Name | GitHub username | Responsibility |
|---|---|---|---|
| 1 | Name | Username | Overview |
| 2 | Name | Username | Programme |
| 3 | Name | Username | Publicity |
| 4 | Name | Username | Logistics |
```

Replace the examples with your group’s details. Add Member 5 if needed.

### Activity 5D — Stage, commit and push

```bash
git status
git add event.md team.md
git diff --staged
git commit -m "Add initial event plan and team details"
git status
git push -u origin setup/event-files
```

Explanation:

- `git add` selects changes for the next commit.
- `git diff --staged` shows what will be included.
- `git commit` records the selected changes locally.
- `git push` sends the commits to GitHub.
- `-u` sets the upstream branch, so you can normally use `git push` for subsequent updates.

### Activity 5E — Create and merge the setup PR

On GitHub:

1. Open Pull requests.
2. Create a new PR.
3. Set base to `main`.
4. Set compare to `setup/event-files`.
5. Give the PR a clear title.
6. Check Files changed.
7. Ask another member to review the changes.
8. Merge the PR after review.

The base branch receives the changes. The compare branch contains the proposed changes.

Select Create a merge commit if the option is available.

### Activity 5F — Everyone: update local `main`

```bash
git switch main
git pull --ff-only origin main
git status
```

Check that `event.md` and `team.md` are now in your local repository.

The coordinator must also do this. Merging on GitHub does not automatically update your computer.

### Group checkpoint

- [ ] The setup PR has been reviewed and merged.
- [ ] Everyone has updated local `main`.
- [ ] Everyone can open `event.md` and `team.md`.

---

## 6. Prepare Your Individual Contribution

### Activity 6A — Create your feature branch

After updating `main`, run only the command assigned to you:

| Member | Command |
|---|---|
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

Make sure you are on your feature branch, not `main`.

### Activity 6B — Create your document

Use your assigned filename.

Include:

- A suitable heading.
- At least two sections.
- At least five useful planning points.
- One assumption or question for the group to discuss.

For example:

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

Prepare your own content. Do not edit `event.md` yet.

### Activity 6C — Commit and push

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

A new file is initially untracked and does not appear in the usual `git diff` output. Stage it first, then inspect it with `git diff --staged`.

### Individual checkpoint

- [ ] My document has been committed.
- [ ] My working directory is clean.
- [ ] My branch is available on GitHub.

---

## 7. Create a PR and Respond to Feedback

### Activity 7A — Create your PR

Use these branch settings:

```text
base: main
compare: your feature branch
```

Give the PR a clear title and use this description:

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

### Activity 7B — Review another member’s work

Read the PR description and Files changed.

Provide:

- One useful question or suggestion.
- One comment on something clear or helpful.

Example:

> The activity sequence is clear. Could you add the estimated duration for each activity so we can check whether the programme fits within the available time?

Do not approve the PR without checking the changes.

### Activity 7C — Respond to the review

Make the improvement on the same feature branch.

Save the file, then run:

```bash
git diff
git add programme.md
git diff --staged
git commit -m "Add activity durations following review"
git push
```

Use your actual filename and a suitable message.

The existing PR will be updated. Do not create another PR for this change.

The reviewer checks the update and approves it when ready.

Do not merge the individual PRs yet.

### Group checkpoint

- [ ] Everyone has created a PR.
- [ ] Everyone has reviewed another member’s work.
- [ ] Everyone has made an improvement following review.
- [ ] All PRs are ready for integration.

---

## 8. Combine the Group’s Contributions

### Activity 8A — Merge Member 1’s PR first

After review, another member merges Member 1’s PR on GitHub.

Everyone waits until this is done.

### Activity 8B — Member 2: update your feature branch

Stay on your feature branch and make sure there are no uncommitted changes.

```bash
git status
git fetch origin
git merge origin/main --no-edit
git status
git log --oneline --graph --all -12
git push
```

Explanation:

- `fetch` downloads the latest remote updates.
- `origin/main` is your local record of the remote `main`, refreshed by fetching.
- `merge` combines that version with your current branch.
- `--no-edit` accepts the generated merge message if needed.

```text
Direction of the merge:

origin/main → feature/programme
```

This does not merge your feature branch into `main`.

As the initial contributions are in separate files, they should combine without a conflict.

The reviewer checks the updated PR and merges it.

### Activity 8C — Continue in member-number order

Members 3, 4 and 5 take turns:

1. Wait for the previous PR to be merged.
2. Fetch the latest changes.
3. Merge `origin/main` into your feature branch.
4. Check the result and push.
5. Obtain review and merge the PR.

Member 1 will practise command-line merging in the next activity.

### Activity 8D — Everyone: update local `main`

```bash
git switch main
git pull --ff-only origin main
git status
```

### Group checkpoint

- [ ] All contribution PRs have been merged.
- [ ] Everyone has all the planning documents locally.
- [ ] Everyone’s working directory is clean.

### Discussion

Explain to another member:

1. What did `fetch` do?
2. What did `merge` do?
3. Why did everyone still need to pull after the PRs were merged on GitHub?

---

## 9. Set Up a Merge Conflict

Each member must resolve a conflict personally. Follow the sequence carefully.

### Activity 9A — Start from the same version

Everyone runs:

```bash
git switch main
git pull --ff-only origin main
git status
```

Check that `event.md` still contains:

```text
Organisers: To be confirmed.
```

Wait until everyone reaches this point.

Do not merge any other changes yet.

### Activity 9B — Create your conflict branch

Use your own member number:

```bash
git switch -c conflict/member-1
```

The other members use `conflict/member-2`, `conflict/member-3` and so on.

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

- [ ] Everyone has created their conflict branch.
- [ ] Everyone has committed a different replacement for the same line.
- [ ] Everyone has pushed and created a PR.
- [ ] None of these PRs has been merged.

The coordinator continues only after all members have reached this checkpoint.

### Activity 9C — Coordinator: update the shared version

Your personal conflict work has already been committed. Create a separate branch:

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

---

## 10. Resolve the Conflict

Proceed in member-number order.

Each member waits until the previous member’s resolved PR has been reviewed and merged.

### Activity 10A — Merge the latest shared version

Use your own branch name:

```bash
git switch conflict/member-1
git status
git fetch origin
git merge origin/main --no-edit
```

Start only when there are no uncommitted changes.

Git should report a conflict in `event.md` and pause the merge.

Do not run another pull or start another merge.

Check:

```bash
git status
```

Git should identify `event.md` as an unmerged file.

### Activity 10B — Read the conflict markers

Member 1 should see something similar to:

```text
<<<<<<< HEAD
Organisers: Member 1.
=======
Organisers: Team coordinator.
>>>>>>> origin/main
```

| Marker | Meaning |
|---|---|
| `<<<<<<< HEAD` | Start of the current branch’s version. |
| `=======` | Divider between the two versions. |
| `>>>>>>> origin/main` | End of the incoming version. |

### Activity 10C — Decide the final content

Keep everyone already listed on `main`, then add yourself.

Member 1 resolves the line to:

```text
Organisers: Team coordinator, Member 1.
```

After that PR is merged, Member 2 resolves the line to:

```text
Organisers: Team coordinator, Member 1, Member 2.
```

Continue in this order until all members are included.

Remove all conflict markers and check the whole file.

Do not simply keep your own version if doing so removes another member’s accepted contribution.

### Activity 10D — Complete the merge

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

The `--check` option can identify conflict markers and whitespace issues, but it cannot tell whether your final content is correct.

### Activity 10E — Review and merge

The reviewer checks that:

- All conflict markers have been removed.
- Previously accepted organisers are still listed.
- The current member has been added.
- No unrelated content has been removed.

Merge the PR.

Only then should the next member start Activity 10A.

### If you need to cancel the merge

To cancel a merge that is still in progress:

```bash
git merge --abort
```

Changes made while resolving the conflict may be discarded.

Ask your instructor for help if you are unsure.

### Final conflict checkpoint

After all members have completed the activity, everyone runs:

```bash
git switch main
git pull --ff-only origin main
git status
```

- [ ] The organiser line includes everyone.
- [ ] Each member has personally resolved a conflict.
- [ ] Everyone’s local `main` is updated.
- [ ] Everyone’s working directory is clean.

---

## 11. Check Your Git History

Run:

```bash
git log --oneline --graph --decorate --all -25
```

| Option | Purpose |
|---|---|
| `--oneline` | Show compact commit summaries. |
| `--graph` | Draw branch and merge relationships using text. |
| `--decorate` | Show branch and other reference labels. |
| `--all` | Include history reachable from all local references. |
| `-25` | Limit the display to 25 commits. |

Find:

1. One of your content commits.
2. A commit made by another member.
3. A merge commit.
4. Your conflict-resolution commit.

Inspect a commit using its actual ID:

```bash
git show COMMIT_ID
```

Replace `COMMIT_ID` with an ID from your repository.

Explain to another member:

- What changed in the commit?
- How do you know?
- What decision did your conflict-resolution commit record?

---

## 12. Independent Group Practice

For this activity, your group decides how to organise the work. No command sequence or branch plan is provided.

### Scenario

Your proposal has been accepted, but the organising committee now requires:

- A half-day event for 120 students.
- A replacement venue, as the original venue is unavailable.
- Accessible and inclusive arrangements.
- Environmentally responsible planning.
- A total budget not exceeding SGD 800.

Your documents must form one consistent event proposal.

### Required outcome

Address the following:

- Purpose and target audience.
- Programme.
- Replacement venue and assumptions.
- Logistics for 120 students.
- Accessibility and inclusion.
- Environmental arrangements.
- Budget.
- Publicity and registration.
- Risks and contingency arrangements.

Clearly labelled estimates are acceptable. You do not need to obtain quotations or make bookings.

Update `event.md` to link to the relevant documents. Keep these practical instructions in `README.md`.

### Collaboration requirements

- Each member contributes at least two PRs during this activity.
- Each member improves a document originally prepared by someone else.
- Every PR receives useful review feedback.
- At least two branches are developed at the same time.
- At least one feature branch is updated with another member’s merged work.
- The group resolves one additional conflict arising from useful, competing edits.
- The agreed proposal is merged into `main`.
- Everyone finishes with an updated local `main` and no uncommitted changes.

Do not make meaningless changes just to create a conflict.

### Additional requirement at the midpoint

After the first round of revised PRs has been merged:

> The event must be able to continue indoors if it rains. The budget remains SGD 800, and attendance remains 120 students.

Decide which documents need to change and coordinate the revisions.

### Evidence to retain

Make sure your repository shows:

- Each member’s contributions.
- Review comments and responses.
- Follow-up commits.
- The additional conflict and its resolution.
- How shared changes were brought into an ongoing feature branch.

You will use this evidence in your retrospective and demonstration.

---

## 13. Reflection and Submission

Create `retrospective.md` and submit it through a reviewed PR.

Include the following:

| Section | What to include |
|---|---|
| Group workflow | How you divided work, used branches, reviewed changes and merged PRs. |
| Individual contributions | Each member’s PR links, contribution and reviewer. |
| Review improvement | The original content, feedback and resulting improvement. |
| Additional conflict | The competing edits, agreed resolution, reason and evidence. |
| Branch update | An example of bringing shared changes into a feature branch. |
| Difficulty and recovery | What happened, what you checked and how you recovered. |
| Midpoint requirement | How the rain contingency affected the plan. |
| Future improvements | Three specific improvements to your group’s workflow. |
| Individual reflection | A task completed independently and a skill to practise further. |

### Final group checklist

- [ ] All required planning areas are covered.
- [ ] Figures and decisions are consistent across documents.
- [ ] The attendance, budget and rain-contingency requirements are met.
- [ ] Every member has the required PR and review evidence.
- [ ] No conflict markers remain.
- [ ] No passwords or access tokens are included.
- [ ] Final changes and the retrospective have been merged.
- [ ] Everyone’s local `main` is updated and clean.

### Submit the following

1. Shared repository address.
2. Member names and GitHub usernames.
3. Link to the final `event.md`.
4. Link to `retrospective.md`.
5. Link to the additional conflict-resolution PR.
6. Any incomplete requirements or outstanding issues.

Make sure your instructor can access the repository.

---

## 14. Demonstration and Assessment

Prepare an 8–10 minute group demonstration.

Every member must explain and show some of their own work.

| Segment | Suggested duration |
|---|---:|
| Final event plan | 1 minute |
| Individual contributions | 3 minutes |
| Improvement following review | 1 minute |
| Conflict and resolution | 2 minutes |
| Difficulty, recovery and reflection | 1–2 minutes |

Show how the work developed, not just the final documents.

Include:

- PR descriptions.
- Changed files.
- Review comments.
- Follow-up commits.
- Conflict-resolution evidence.
- Your current branch and local working state.

### Assessment criteria

| Criterion | Weight |
|---|---:|
| Individual Git participation | 20% |
| Pull requests and review | 20% |
| Merging and conflict resolution | 20% |
| Independent practice outcome | 20% |
| Evidence and reflection | 10% |
| Individual understanding | 10% |

More commits or larger PRs do not automatically mean better work. A conflict is not a failure; what matters is how you resolve it.

---

## 15. Troubleshooting Reference

Before trying a fix:

1. Read the error message.
2. Run `git status`.
3. Check your current branch.
4. Confirm what you intended to do.
5. Preserve your work before making further changes.

| Problem | What to check first |
|---|---|
| “Not a Git repository” | Check your location and enter the cloned project folder. |
| Local changes would be overwritten | Run `git status` and `git diff`. Preserve your work before continuing. |
| Changes are missing on GitHub | Check whether you saved, staged, committed and pushed. Also check the branch shown on GitHub. |
| Push is rejected | Read the error. Check access, authentication and whether the remote branch has newer commits. Do not force-push. |
| `pull --ff-only` refuses | Check the history and ask for help. Preserve any local commits. |
| Unexpected files appear in a PR | Check the base branch, compare branch and branch history. |
| A conflict is still unresolved | Check every unmerged file, agree on the final content, remove markers, stage and commit. |

### If your remote feature branch has newer commits

If someone has pushed commits to the same feature branch, you may need to fetch and merge that matching branch before pushing.

For example, while on `feature/programme`:

```bash
git fetch origin
git merge origin/feature/programme --no-edit
```

Resolve any conflict, complete the merge if needed, then push.

Use your actual branch name. Do not use this as a fix for an authentication or permission error.

### Common commands

| Command | Purpose |
|---|---|
| `git clone URL` | Create a local copy of an existing repository. |
| `git status` | Check your branch and working state. |
| `git branch --show-current` | Show the current branch name. |
| `git switch main` | Switch to local `main`. |
| `git switch -c feature/name` | Create and switch to a branch. |
| `git diff` | Check unstaged changes to tracked files. |
| `git add FILE` | Stage a file’s changes. |
| `git diff --staged` | Check changes selected for the next commit. |
| `git commit -m "Message"` | Record staged changes locally. |
| `git push -u origin BRANCH` | Publish a branch and set its upstream. |
| `git push` | Push to the configured upstream. |
| `git fetch origin` | Download remote updates without integrating them. |
| `git pull --ff-only origin main` | Update local `main` when a fast-forward is possible. Use while on `main` in this practical. |
| `git merge origin/main --no-edit` | Bring the fetched remote `main` into your current branch. |
| `git merge --abort` | Cancel a merge that is still in progress. |
| `git log --oneline` | View compact commit history. |
| `git show COMMIT_ID` | Inspect a particular commit. |

---

## 16. Individual Completion Checklist

- [ ] I cloned the shared repository.
- [ ] I created and switched to my own branch.
- [ ] I checked changes before committing.
- [ ] I staged and committed my own work.
- [ ] I pushed my branch to GitHub.
- [ ] I created a PR.
- [ ] I reviewed another member’s work.
- [ ] I responded to review feedback.
- [ ] I updated local `main` after a GitHub merge.
- [ ] I merged shared changes into a feature branch.
- [ ] I personally resolved and committed a conflict.
- [ ] I can find and explain one of my commits.
- [ ] I contributed to the independent group practice.
- [ ] My local `main` is updated and my working directory is clean.

### Individual reflection

Include your responses in `retrospective.md`:

1. What task can you now complete on your own?
2. What useful feedback did you receive or provide?
3. What mistake did you learn from?
4. Which Git skill would you like to practise further?

---

## 17. Optional Extension Activities

Attempt these only after completing the required work.

### A. Improve the handover

A new committee member has five minutes to understand your plan.

Improve navigation so they can find:

- The event summary.
- The programme.
- The budget.
- Contingency arrangements.
- Outstanding decisions.
- The member responsible for each planning area.

Ask another group to find all six without your help.

### B. Review an incomplete proposal

Prepare a realistic but incomplete improvement, such as:

- A programme without transition time.
- A budget missing an expense.
- A publicity plan without registration details.

Submit it as a PR.

The reviewer identifies the issue and its consequence. The author improves the proposal before it is merged.

### C. Coordinate overlapping work

Two members independently improve the same section with useful but different proposals.

Produce one consistent final version.

Explain:

- What each member intended.
- Where the proposals overlapped.
- What the group kept, changed or removed.
- Why the final version was suitable.

### D. Review another group’s repository

Exchange repository links with another group.

Without a verbal explanation, identify:

- One strength.
- One inconsistency.
- One missing detail.
- One question affecting whether the event can be carried out.

Discuss which feedback to accept and implement the changes through reviewed PRs.

---

## Closing Reminder

The aim is not to memorise every command. Develop the habit of understanding your current state, making focused changes, checking the result and sharing work carefully.

```text
Check → Update → Branch → Edit → Inspect → Commit
      → Push → Review → Improve → Merge → Synchronise
```
````
