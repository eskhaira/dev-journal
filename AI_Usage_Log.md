## AI usage log for P1L4

- It was not clear to me that i could research the docs so i pushed claude to give me the method. Next time i need to read the docs. My mistake was thinking that was against the rules
- I need to take my frustrations out in the gym, not on claude.

## AI usage log for P1L5 - Non coding help

- so before I began the lesson, me and Claude hardcoded a few rules first the solo builds will require one or two concepts from past lessons to be demonstrated while maintaining the core idea of the current lesson as the main focus.
- we talked about increasing the pace of the apprenticeship. The rule going forward is this - Claude will grade me on five things.

1. One, main stays sealed — every change lands through a merged PR, descriptive branch names, no exceptions.
2. Two, when something breaks, mistakes.md gets opened before any AI does.
3. Three, the AI usage log is written the same session, not reconstructed later.
4. Four, teach-backs and retrieval reps happen without claude chasing me.
5. Five, no silent weeks — if i'm on the road, cab drills are running. That last one is a habit too, not just a retention trick.

- current grade is C+. Aim is A by mid july.

- No AI usage logs for L1-L3. Stupid lazy me. L4 was very brief, getting serious with L5 moving forward.

- hit a deprecation on React.FormEvent, asked for the why after reading the diagnostic.
  Claude said: The browser — the actual DOM spec — has no event called FormEvent. Never did. When a form submits, the platform fires a SubmitEvent. When an input changes, an InputEvent. React wraps these native events in its own synthetic wrapper, and years ago React's type definitions invented one vague bucket type called FormEvent to cover all of them. It papered over what the platform really does. The types maintainers are now renaming to match reality

## AI usage log for P1L5 - Coding Help

When i got stuck at 4rth guard rail test, i asked claude for help. Claude told me to run these three to check their outputs in the console. That would help me determine why my guard rails were failing.

1. Number("")
2. Number.isNaN(Number(""))
3. Number(" ")

I also did not follow the instructions to explain my workflow, just plainly went to fixing the error. The whole workflow explanation is inside mistakes.md

Claude also told me to do these minor fixes:
Placeholders at line 76/82/91 updated with proper casing. SearchText changed to Search Transactions
description needed to be added as trimmed. So line 56 became `description: description.trim(),`

## AI usage log for P1L5 - Solo Build

- I asked claude to explain the requirements in detail
- I also asked claude about how i am thinking about doing this - Every amount entered by the user will be rounded off to 2 decimal places, then multiplied by 100 and then stored as an integer? And then to display dollars, we divide by 100 and show as a float?
- I looked up MDN for the method claude suggested as follows: "So the thing you render can't be a number at all — it has to be a string, formatted to exactly two places. Go find the method on MDN that turns a number into a fixed-decimal string"
