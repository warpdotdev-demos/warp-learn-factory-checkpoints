# Triage

Classify the goal: an answer, a requested change, or unclear. For a change, research it, assess its complexity, and find or create the tracking issue. Recommend a spec when the change is a new feature, touches several areas, or leaves behavior choices open. For an answer, the evidence-backed answer is the deliverable.

1. Research. Read the request and the attached material. Read the applicable code. Make sure that you understand what is asked and where the problem or the change is. If you cannot clearly identify the problem, ask the foreman to obtain more information.
2. Depending on the type of request, you may need to:
   - For a bug report: if the research in step 1 identifies the cause, a reproduction is not necessary. If the cause is not clear from the research, reproduce the bug if you can.
   - For a feature request: identify the requirements.
   - For a question: return the evidence-backed answer to the foreman; do not turn it into an implementation plan. Track the underlying problem only if it deserves an issue.
3. Issue decision. Decide if the work needs an issue. If the work is too small to track, skip the issue, note that, and end the stage; the conversation is the record.
4. Find or create the issue. If the request came from an issue, adopt it. Otherwise search for an existing issue that tracks the same work, and adopt a clear match. If the request is a follow-up to work already in progress (an open factory PR, or an issue already moving through the factory), adopt that work instead of creating a parallel issue. If there is no clear match, create a new issue. Keep the issue URL at hand; every later stage needs it.
5. For a new issue, follow the issue content template below. For an adopted issue, add what you learned as a comment.

Use the `gh` CLI for GitHub issues: `gh issue list --search` to find existing work, `gh issue create` to file an issue, and `gh issue comment` to record your findings on one.

## Issue content

Write a clear, concise title that describes the work.

For the issue description, adopt the style of existing issues if there is a consistent one. Otherwise, use this template, omitting sections that do not apply:

    ## Description
    What is wrong or what is asked, and where. Human-readable.

    ## Reproduction
    The reproduction steps and proof: the output of the failed test, the incorrect response, or the visual proof. When research identified the cause without a reproduction, the explanation and the evidence instead.

    ## Acceptance criteria
    The checks that show that the work is complete.

    ## Candidate approaches
    The approaches you considered, each with its trade-off, and the one you recommend and why. This is input to the next steps, not a decision.

    ## References
    Specific code locations, test results, error output, and applicable links.

The References section is important: without it, the later stages have to collect this context again, which is slow and costly.

## Complexity, ambiguity, and choices

- Report the complexity as a t-shirt size:
  - XS or S: the change is local and obvious, with low risk.
  - M: the change touches multiple files, with bounded uncertainty.
  - L or XL: the change is cross-cutting, has risk, or is a full feature.
- Tell three kinds of uncertainty apart, and report each in its own place:
  - Facts that research can settle (where the bug is, what the code does today, which callers are affected) are not ambiguity. Settle them and record the evidence.
  - Behavior choices (more than one behavior is reasonable, or the request leaves out important requirements) are ambiguity. Report them.
  - Approach choices (more than one reasonable way to do the work, with trade-offs a user would care about) go in the candidate approaches.
- Do not invent ambiguity where the request is clear, and do not hide a real choice by picking for the user. Both are errors; the second is the more expensive one.
