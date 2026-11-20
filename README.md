# Warp Learn factory checkpoints

Reference factory definitions for [Build a self-improving software factory](https://www.warp.dev/learn). Each folder is the complete factory definition at the end of one Unit 2 lesson, so you can compare it with yours or start a lesson from a known-good state.

| Folder | Lesson |
| --- | --- |
| [`unit-2-lesson-1-hello-factory`](unit-2-lesson-1-hello-factory) | Hello factory |
| [`unit-2-lesson-2-connect-an-issue-backlog`](unit-2-lesson-2-connect-an-issue-backlog) | Connect an issue backlog |
| [`unit-2-lesson-3-tackle-larger-features-with-specs`](unit-2-lesson-3-tackle-larger-features-with-specs) | Route work with triage and specs |
| [`unit-2-lesson-4-add-verification-and-merge-risk`](unit-2-lesson-4-add-verification-and-merge-risk) | Add verification and merge risk |
| [`unit-2-lesson-5-close-the-loop-with-alert-monitoring`](unit-2-lesson-5-close-the-loop-with-alert-monitoring) | Close the loop with alert monitoring |

The app these factories work on is [warp-learn-markdown-app](https://github.com/warpdotdev-demos/warp-learn-markdown-app).

## Using a checkpoint

Copy the contents of a folder into your factory definition, then replace the placeholders:

- `YOUR_GITHUB_ORG`: the GitHub org or user that owns your copy of the markdown app (in `factory.yaml` and `automations/github-issues/automation.md`).
- `YOUR_WEBHOOK_UID` (lesson 5): the ID at the end of your error monitor webhook URL.

The checkpoints use GitHub Issues for the backlog. If you followed the Linear path in lesson 2, keep your `automations/linear-issues/automation.md` in place of `automations/github-issues/`.
