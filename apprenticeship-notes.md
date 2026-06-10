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

## Solo Build P1L3 Question Answers

1. The user clicks the "Clear All" button.
2. When the button is clicked, all transactions on the page should be gone. Clear empty list should be displayed
3. yes that data is already state when we defined the `const [transactions, setTransactions]=useState(....)`
4. So i need to build a new function that changes the data to an empty list
5. The function just creates a new empty array. I did it by `setTransactions([]);`

## P1L3 - Explain the state + delete flow in 100 words

The logic went like this. The transaction array holding the transactions must be in state so we defined the `const [transactions, setTransactions]=useState(........//transactions inside)`. `transactions` hold the original array and `setTransactions` is what tells react what changed so react can re-render. Then we needed a function to handle the change of deleting the transaction. We receive the id of that transaction, then we create a new array by filtering out that transaction that the id is pointing towards from the original array and then we call setTransaction with the new array inside. That function is then passed to the `<Transactions>` component as props to display the delete button in front of every transaction along with the passed prop to perform the delete when the button is clicked. When we call the component as JSX, we can pass our defined function as a prop inside the component.

## P1L4 - Initial Notes

Never store what you can derive.
Value displays, onChange writes, and onChange only fires when the user acts.

## AI usage log for P1L4

- It was not clear to me that i could research the docs so i pushed claude to give me the method. Next time i need to read the docs. My mistake was thinking that was against the rules
- I need to take my frustrations out in the gym, not on claude.

## P1L4 - 100 words

The whole point of controlled input is to compute on each keystroke pressed by the user. The text from the input field needs to live in state. A controlled input works with two levers, value and onChange. Value points towards the state variable in which the text needs to live and onChange watches for user input (keystrokes), fires as soon as a single key is pressed, updates the state variable and react re-renders the whole app() component. When user types, onChange fires and stores that value in the declared state variable, react re-renders. As another key is pressed, onChange fires again, value in the state variable is replaced and react re-renders again.
