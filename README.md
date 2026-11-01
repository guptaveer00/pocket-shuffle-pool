# Pocket Shuffle Pool — Phase 1

Designed by **Veer Gupta**. Phase 1 foundation built with Codex assistance; Sai will extend this project in Phase 2.

## Run

No dependencies or build step. Download/extract or clone the repository, then open `index.html` in a current desktop Chrome, Firefox, Safari, or Edge browser. Keep the `js/` folder and `style.css` beside it. Alternatively, run `python3 -m http.server 8000` in this folder and visit http://localhost:8000.

## Play the foundation

Move the mouse over the table to aim. Hold the left mouse button to charge (maximum power at 1.2 seconds), then release to shoot toward the pointer. Wait for all balls to stop before the next shot. Reset table restores the starting layout. Desktop mouse controls are the target; touch controls are not tested.

This is a physics sandbox, not a completed match. Pockets are visual markers only: all edges currently rebound balls, including the open-looking pockets. No balls can be pocketed yet, and there are no player turns, fouls, winner, or pocket shuffle.

## Acceptance criteria at handoff

Numbers below follow the order of the acceptance-criteria bullets in SPEC.md.

1. **Partially met:** table and all eight balls load and shots work; a complete pool match is not playable yet.
2. **Met:** mouse aims with an initial-direction line.
3. **Met:** holding/releasing charges/shoots; the visible meter caps at 1.2 seconds.
4. **Met:** fixed-step circle physics includes cushion rebounds, collisions, and friction; simplified rather than realistic.
5. **Met:** another shot is blocked while balls move; repositioning is not implemented.
6. **Partially met:** four open and two covered pocket markers render; actual pocket removal is missing and all boundaries rebound.
7. **Not met:** completed shots are counted, but pockets do not shuffle.
8. **Not met:** no active player or assignment state/HUD yet.
9. **Not met:** no pocket events or turn resolution yet.
10. **Not met:** no scratches or cue-ball placement yet.
11. **Not met:** no 8-ball eligibility or win/loss rules yet.
12. **Not met:** no game-over state or winner display yet.
13. **Partially met:** motion/charging status and completed-shot count display; player progress, shuffle countdown, and foul messages are missing.
14. **Partially met:** reset restores existing ball/pocket layout and shot count; future match state must also reset.
15. **Met:** stripes and number labels distinguish balls; crossed covers distinguish closed-pocket markers from open ones.

## Code map

- `index.html`: page structure; scripts load in dependency order.
- `style.css`: responsive page and table styling.
- `js/physics.js`: `PoolPhysics.bounds`, ball radius, movement check, and `step(balls, dt)` for cushions, equal-mass collisions, and friction.
- `js/game.js`: `create()` returns fresh balls/pockets/shot state, `shoot()` guards and applies velocity, `update()` advances physics and detects the end of a shot. Add turn resolution here.
- `js/render.js`: draws table, pocket markers, cue/aiming line, and balls. Ignores balls flagged `pocketed`.
- `js/main.js`: pointer input/capture, charging, reset, status display, animation loop with 1/240-second physics steps.

These scripts expose `window.PoolPhysics`, `window.PoolGame`, and `window.PoolRender` to avoid a module server/build dependency. Preserve script order.

## Sai's next steps, in priority order

1. Read SPEC.md and run this foundation before changing it. Commit the unchanged received project as the first commit in your own NEW repository.
2. Add pocket detection BEFORE cushion response in `physics.js`. Record pocketed ball IDs for the current shot; use the existing `pocketed` flag. Closed pockets should retain their rebound behavior.
3. In `game.js`, change the closed pair after every second completed shot, only after motion stops. Choose a different pair, keeping exactly two closed.
4. Add current-player/group state, remaining-ball counts, and shot resolution. Capture 8-ball eligibility at the START of a shot; resolve scratches and early/simultaneous cue-and-8 losses before offering another shot.
5. Add valid cue-ball placement after scratches, winner display/input blocking, and full reset. Extend the renderer/HUD to show the new state.
6. Test complete matches and update each acceptance-criterion status honestly. Keep a Phase 2 prompt log and personally write HANDOFF_REPORT.md without AI.

## Known limitations and shortcuts

- Pocket artwork sits on continuous rectangular cushions. Opening a pocket visually does not make a physical opening; implementing this is the first major missing feature.
- Circle collisions have no spin or angular momentum. Small fixed steps reduce tunneling, but crowded wall-contact cases may still overlap/jitter briefly; edge handling precedes pair separation.
- The starting rack is a compact seven-ball layout, not a regulation rack.
- Minimum shot power is nonzero; even a short click shoots. Moving the pointer while charging changes the release direction.
- Switching tabs or cancelling a pointer cancels charging. A paused tab's physics advances at most 0.05 seconds on return.
- Game logic and rendering are deliberately separate. The `pocketed` field and end-of-shot TODOs are extension points, not completed rules.
- No third-party dependencies, audio, assets, AI opponent, or advanced pool rules. This leaves time for the central mechanic and playable rules in Phase 2.

## Verification

JavaScript syntax and headless physics checks cover initial counts, shooting lockout, shot settling/counting, velocity transfer, and cushion rebound. Browser preview loaded successfully and a held click produced ball movement; reset was checked in the browser, and shot completion was checked in the headless simulation. Full match/pocket/shuffle behavior cannot be verified because those features are not implemented.
