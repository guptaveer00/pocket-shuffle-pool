# Phase 1 prompt log

## Tools and model

OpenAI Codex desktop assistant; exact underlying model/version was not exposed in this chat. Tools used: local shell/Git, file editing, JavaScript execution for physics checks, and browser automation for preview. Implementation uses vanilla HTML/CSS/JavaScript with no external game library or generated assets.

## Important prompts (verbatim, chronological)

> what about 8 pool ball, but the twist can be like idk?

> yeah okay i like the pocket suffle, yeah keep it 2D, and yea for scope the 3 solids 3 stripes, and 8 ball is good.

> yes the rules is its two players on same computer, shuffle evetying 2 shots, yes 4 open and 2 closed, yes for the wining, yes for the fouls. write the sepc.md for me (i asked the prof he says its okay cuz i missed class ) and im confused do i commit the spec to a repo or something?

> can u do this all for me please. and do i send sai the repo when there is just the spec or like after some code and stuff.

> undo this stuff, ill make the repo and stuff

> okay i move the spec to the desktop, so we can use vsc code as well. cretaed this:
> [https://github.com/guptaveer00/pocket-shuffle-pool](https://github.com/guptaveer00/pocket-shuffle-pool)
>
> do the first step of making the commit of the spec. thats the first step right?

> okay do this for me, build out a bit

## What happened

The assistant suggested pool twists; Veer chose Pocket Shuffle and confirmed the core rules. The assistant drafted SPEC.md after Veer reported professor approval. The first commit contains SPEC.md only.

On the earlier broad request, the assistant built a starter before Veer asked to undo that work and handle the repository setup himself. The starter commit/files were removed, preserving the spec-only first commit. Veer then created the GitHub repository and explicitly requested the spec commit be pushed. On the latest request to build a bit, the assistant restored that starter foundation and documented it. The final history should be read as the actual retained Phase 1 work, not the abandoned attempt.

Veer also edited SPEC.md on GitHub before implementation; those edits are preserved ahead of the code commits.

The current code intentionally stops at aiming/shooting/basic physics. The assistant did not implement a finished game, and the README lists the missing pocket mechanics, shuffle, turns, fouls, and winning. Sai should use scoped requests and review diffs to preserve this foundation.
