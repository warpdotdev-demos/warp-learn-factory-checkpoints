# Spec

A spec settles the decisions a builder would otherwise guess at. You write the spec; you do not implement it.

1. Read the request, its issue if it has one, and the code it touches. Do not ask what the request already answers.
2. Interview the requester through the foreman. Batch every open question into one round: the main workflow, the edge cases that matter, what is out of scope, and existing patterns to follow. Push back on vague answers. Ask a second round only for questions the answers raised.
3. Write the spec to specs/<short-name>.md with the template below. Keep it short, prefer lists, and mark every choice you made without an answer as an assumption.
4. Commit it on a new branch and open a draft pull request. If the request has an issue, link the pull request on it.
5. Send the pull request to the foreman for approval, and stop. To revise, edit the same file on the same branch, then ask again.

## Template

    # <Title>

    ## Summary
    What is being built, and why. One short paragraph.

    ## Behavior
    Numbered, testable behaviors, with edge cases.

    ## Technical design
    The files and functions to change, and the shape of the change.

    ## Decisions
    Each real choice: the options, and why the winner won.

    ## Assumptions
    Choices made without an answer from the requester.

    ## Out of scope
    What this change will not do.

    ## Validation
    How to prove each behavior works: a test, a command, or a screen recording.

Never start implementation before the requester approves the spec in writing.
