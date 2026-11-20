---
name: ui-verification
description: Prove a user-facing change works by driving the running app with computer use, and add a Visual proof section to the pull request description.
---
# UI verification

Use this whenever a change affects something a user can see or click.

## Start the app

1. Run `MARKY_DESKTOP_ENABLE_CDP=1 pnpm dev:desktop`.
2. Read the terminal output for:
   - `Playground: <path>`
   - `DevTools listening on ws://*********:9222/...`
3. Use the auto-opened editable playground at `apps/desktop/.dev-electron/playground` instead of file pickers or checked-in fixtures.

## Walk the path

4. Walk the exact path the request describes. For a bug, show the symptom is gone. For a feature, show the new behavior and its key interactions.
5. Use computer use to see and record the app. Prefer the Chrome DevTools Protocol endpoint for interaction-heavy steps: it can inspect DOM state, evaluate JavaScript, click controls, inspect iframe contents, and capture screenshots from the real Electron renderer. This helps when computer use has trouble interacting with the dev app window.
6. For CDP, fetch `http://*********:9222/json/list`, connect to the page's `webSocketDebuggerUrl`, and drive the renderer with DevTools Protocol commands.

## Record the proof

7. Record a video of the flow. Add a screenshot only for a final state worth inspecting closely, like a pixel-level visual fix.
8. Add a `## Visual proof` section to the pull request description: the path you walked, what each recording or screenshot shows, and the media itself. Never commit media to the branch.
9. If the app cannot launch or the path cannot be reached, say so in the Visual proof section. Never claim a verification that did not happen.
10. When you are done, stop the dev server and confirm no `Marky Dev` process remains.

## Gotchas

- Build `packages/ui` and `packages/editor` first if you start the app any other way; the desktop app imports their dist output.
- Screenshots are DPR 2: CSS pixels times 2.
- Right clicks need real `Input.dispatchMouseEvent` events; synthetic `contextmenu` events don't open base-ui context menus.
- Popup open in the DOM but missing from a screenshot? Check stacking with `document.elementFromPoint`.
- xterm refits through a debounced ResizeObserver and can lag layout changes by a few seconds; re-measure before calling it a bug.
