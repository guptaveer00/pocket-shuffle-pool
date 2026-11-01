# Pocket Shuffle Pool

## Game overview

Pocket Shuffle Pool is a top-down, 2D pool game for two players sharing one computer. The table contains one cue ball, three solid balls, three striped balls, and the black 8-ball. Player 1 uses solids and Player 2 uses stripes, assigned at the start.

Players aim and choose shot power to pocket their assigned balls, then pocket the 8-ball to win. The twist is that only four of the six pockets are open. After every two shots, two randomly selected pockets become closed and the other four become open. Closed pockets behave like cushions. Players must adapt their next shot to the new layout.

The intended feel is casual and strategic: familiar pool controls with changing opportunities. Simple shapes and clear feedback are enough; realistic graphics and tournament-level physics are outside the scope.

## Controls and shot flow

- Move the mouse to aim from the cue ball toward the pointer.
- Hold the left mouse button to charge shot power, then release to shoot. Power is capped, with a visible meter.
- Aiming and shooting are allowed only when all balls have stopped.
- An aiming line shows the initial direction, without predicting bounces.
- After a cue-ball foul, the incoming player clicks a valid location on the table to place the cue ball before aiming.
- A visible Restart button starts a fresh game.

## Rules

1. Two local players alternate turns, with Player 1 starting.
2. Each player has three assigned balls: solids for Player 1, stripes for Player 2.
3. Pocketing at least one of your own balls lets you shoot again, unless you foul. Otherwise, the turn passes to the other player.
4. Pocketing an opponent's ball removes that ball and counts toward their progress. It does not by itself earn another shot.
5. There are six pockets, with exactly four open and two closed from the start. Closed pockets block balls like the surrounding cushion.
6. Every completed shot counts toward the shuffle, including fouls and shots that earn another turn. After every second shot, once all balls stop, select a new closed pair randomly from the pairs other than the current pair. Display the new layout before another shot can begin.
7. A player wins by pocketing all three assigned balls and then legally pocketing the 8-ball into an open pocket. The assigned balls must already be cleared before the winning shot begins.
8. Pocketing the 8-ball before you are eligible loses the game. Pocketing the cue ball and 8-ball on the same shot also loses the game.
9. Pocketing the cue ball is a foul. The turn ends, and the opponent may place the cue ball anywhere inside the playing area that does not overlap another ball or a pocket. Other balls pocketed during that shot remain pocketed.
10. To keep the project manageable, there are no additional first-contact, rail-contact, or called-pocket foul rules.

## Intended features

- A single table with cushions and six clearly marked pockets.
- A repeatable starting arrangement with the cue ball separated from the seven object balls.
- Mouse aiming, a direction guide, and adjustable shot power.
- Ball movement, friction, ball-to-ball collisions, and cushion rebounds.
- Pocket detection that removes balls entering open pockets.
- The pocket shuffle mechanic, including closed-pocket rebounds.
- Turn management, assigned ball tracking, cue-ball fouls, and ball placement.
- Win/loss detection and a restart option.
- A HUD showing the current player, group assignments, remaining balls, shots until the next shuffle, and relevant messages.
- Clear visual differences between solids, stripes, the cue ball, the 8-ball, and open/closed pockets.

## Acceptance criteria

1. **[Must]** The game launches using the README instructions and displays a playable 2D table with six pockets, one cue ball, three solids, three stripes, and one 8-ball.
2. **[Must]** The mouse controls aim, and a visible line indicates the cue ball's initial shot direction.
3. **[Must]** Holding and releasing the left mouse button charges and takes a shot, with a visible capped power meter; longer holds produce stronger shots up to the cap.
4. **[Must]** Balls move after a shot, rebound from cushions, collide with other balls, and gradually stop through friction. Simplified physics are acceptable if normal shots behave consistently.
5. **[Must]** The player cannot take another shot or reposition the cue ball while any ball is moving.
6. **[Must]** Exactly four pockets are open and two are closed. Balls entering open pockets are removed; balls hitting closed pockets rebound and remain in play.
7. **[Must]** After every two completed shots, including fouls, the closed-pocket pair changes only after all balls stop. The new pair differs from the previous pair, and exactly four pockets remain open.
8. **[Must]** Player 1 is assigned solids and Player 2 stripes. The current player and assignments are visible.
9. **[Must]** A player continues after pocketing their own ball without fouling; otherwise the turn passes. Opponent balls pocketed on the shot remain removed and update the opponent's remaining count.
10. **[Must]** Pocketing the cue ball ends the turn and allows the opponent to place it. Invalid placements outside the playing area, overlapping balls, or overlapping pockets are rejected.
11. **[Must]** Pocketing the 8-ball wins only if the shooter had cleared their assigned balls before that shot and did not pocket the cue ball. An early 8-ball or an 8-ball pocketed with the cue ball awards the win to the opponent.
12. **[Must]** The game displays the winner and prevents further shots after the game ends.
13. **[Should]** The HUD accurately shows each player's remaining balls and the number of shots until the next shuffle, and announces a shuffle or foul.
14. **[Must]** Restart resets the balls, assignments, current player, shot counter, pocket layout, and game result to a fresh playable game.
15. **[Should]** Ball groups and pocket states are distinguishable using markings as well as color, such as stripes and a closed-pocket cover.

## Priorities and scope cuts

First establish a running table with shooting and dependable basic physics (criteria 1–5). Next implement pocket behavior and the shuffle, since these define the game (6–7). Then complete turns, fouls, and winning so a full match is playable (8–12), followed by restart (14) and HUD/visual refinements (13 and 15).

If time runs short, sacrifice decorative graphics, animation, sound, and extra HUD polish first. Keep the pocket shuffle and basic playable match rules. Document any unmet or partially met criteria honestly.

Not planned: online play, computer opponents, full 15-ball pool, multiple levels, realistic spin, cue elevation, advanced trajectory prediction, sound effects, or mobile controls.

## Planned Phase 1 foundation

Aim to leave a runnable table with the starting balls, aiming and power controls, ball movement, friction, and basic collisions. Separate physics, game rules, and rendering/input into understandable modules where practical. Leave clear extension points for pocket states, turn resolution, and win/loss checks.

The README must report what actually works at handoff, rather than treating this plan as completed work. Sai will use the remaining acceptance criteria and priorities to finish the game within the Phase 2 time budget.
