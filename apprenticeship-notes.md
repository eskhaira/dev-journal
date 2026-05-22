## Future project: Trading & investing dashboard

What it is: Aggregate trading/investing data I currently
check across ~10 sites. Surfaced through AI for summaries,
anomalies, signal-vs-noise filtering.

Why this fits me: I'm already in markets. The pain is real
and recurring. I would dogfood it.

Phase fit: P5 (when AI features come online) or P8 (real
product, real users).

Open questions to research over the next 6 months:

- Which data sources have free or cheap APIs? Which are
  paywalled or rate-limited?
- What do I actually look at across those 10 sites? List
  every signal. Cut to top 5.
- Is this a dashboard, an alert system, or both?
- Who else would use this? Just me, or is there a market?

Decision point: Revisit at the start of P5. Compare against
truck-domain ideas. Pick the one that has the better mix of
"I would use this daily" and "skills I want to build."

## Teachbacks

P1L1 Teach back: what is a React component?

My answer: A React component is basically a JavaScript function that returns JSX and it takes props as an argument. The props inside is a single object, and it could have multiple fields like `props.name`, `props.size`, `props.jobTitle`, `props.age`. This object is passed when we write the component as JSX and provide the required fields it needs. Every component name starts with a capital letter because that's how React knows it's a user-defined component and not an HTML component that is received from the browser.

P1L1 Solo Build - truck-stop-tracker

What you remembered without checking
I remembered that my component needed three fields as one object, and each of those fields needed to be defined. Two of them were strings, and one of them was a number. Then inside the app component, I needed to include my truck stop component and pass four examples, each containing the object with three fields: name, location, and rating.

What you had to look up
Honestly, the only thing I needed to look up was the git command I needed, the `git remote add origin`. I forgot that command, so I needed to look that up.

Where you got stuck (if anywhere)
Same place I got stuck while we were practicing. I initialized the git repository with the README.md file, and when I tried to push from my local repo, it kept giving me errors.I did try to take help from Gemini to clear those errors, but then I realized that I could just delete and re-initialize from the beginning. I had to delete the repository on github.com and then reinitialize everything from the beginning this time without the README.md file.

One thing that surprised you
Nothing. It was pretty generic, although I did get to use something other than a string. For example, for rating I had to use a number, so that was different.
