## Teachbacks

P1L1 Teach back: what is a React component?

My answer: A React component is basically a JavaScript function that returns JSX and it takes props as an argument. The props inside is a single object, and it could have multiple fields like `props.name`, `props.size`, `props.jobTitle`, `props.age`. This object is passed when we write the component as JSX and provide the required fields it needs. Every component name starts with a capital letter because that's how React knows it's a user-defined component and not an HTML component that is received from the browser.

This file will hold all my journal entries for Project One, Lesson One, the coding part and the server setup and machine setup.
So before we began this, We touched up our knowledge on `useState` and how it also resets to the initial value if you refresh the page. If you wanted to store that value, we would need something called `localStorage`, which we will learn in future lessons.
Then we checked git version, node version, and npm version. Everything was up to date.
After that, we ran a command called `npm install vite@latest`. We created a project called Finance Tracker and we CD'd into it
After the install, we went into the files, and the first file we looked at was Index.html I had a doubt. why the script element was not nested inside the div element?
Answer: In HTML, the order of tags determines the order of execution. Code further down the file runs after code earlier in the file. A script tag can reach back and touch anything that came before it in the file, because those things already exist in the DOM by the time the script runs.
So when we write import something inside curly braces, that would pick a specifically named export, but when we write it without any braces, that's the default export and you can name it whatever you want. For example, in the main.tsx file, the strict mode was inside curly braces. It was asking for a specific export, but the app was in no braces, so it was asking for the default export from that file. Also, when we write `import` something from what comes after the `from`, if it starts with a dot, it means it's looking for something inside the current directory. If it starts with something, let's say `react`, no dots, no slashes, it's looking for something inside `node_modules/` for a package called `react`.
When we write `import` and then just simply write `/CSS file` or whatever the name of the CSS file is in the current directory, it just means we are not importing any function or anything. We are just asking React to include the CSS inside this page.
This specific point refers to the main.tsx file. The createRoot says that this is the DOM element where my app is going to live. document.getElementById is finding the root div inside the DOM. Then it creates a react root, which is attached to that div element, and it renders the app component inside it. The strict mode component is a development-only wrapper. When you build the app for deployment, strict mode will do nothing. While developing, it intentionally runs your components twice on every render to surface bugs you will otherwise miss. You'll occasionally see things appear to run twice in dev. That's not a bug; that is strict mode doing its job.

## P1L1 Solo Build - truck-stop-tracker

What you remembered without checking
I remembered that my component needed three fields as one object, and each of those fields needed to be defined. Two of them were strings, and one of them was a number. Then inside the app component, I needed to include my truck stop component and pass four examples, each containing the object with three fields: name, location, and rating.

What you had to look up
Honestly, the only thing I needed to look up was the git command I needed, the `git remote add origin`. I forgot that command, so I needed to look that up.

Where you got stuck (if anywhere)
Same place I got stuck while we were practicing. I initialized the git repository with the README.md file, and when I tried to push from my local repo, it kept giving me errors.I did try to take help from Gemini to clear those errors, but then I realized that I could just delete and re-initialize from the beginning. I had to delete the repository on github.com and then reinitialize everything from the beginning this time without the README.md file.

One thing that surprised you
Nothing. It was pretty generic, although I did get to use something other than a string. For example, for rating I had to use a number, so that was different.

## 2026-05-27 - P1L2 Solo Build

So I performed the solo build. The project is called a book tracker, and it displays lists of books. I had the option to also add another section with books that I want to read. I also did that. I also numbered the list. I had to declare an array of books, and I also had to declare another array called "Books I Want to Read". The first one had five items, and the second one had three items. I also created a book component in a separate file which displays those lists of books. Each component is taken in an object with four fields:

- title
- author
- year
- position
  Then inside the App.tsx file, I am calling the `dot map` function on my `books`, and on `booksToRead` arrays.
  The only problem I had was to number the list, so I came up with the position parameter inside the object, and I rendered that position parameter as an index in the map function call.

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

## P1L4 Solo Build NOTES

- I can use search, official docs but no AI solving anything for me
- I needed to find the particular method for this on MDN.(mozilla docs for javascript). We needed to figure out how to match each typed input in the search field the description of transactions. As the user typed each word, only display the transaction whose description inlcuded those words. So we used `.includes("")`
- I kept trying to match the whole string being typed with the description. The destroyer was `setTransactions(filtered)` overwriting the stored truth with a derived view.
- AI gave Socratic questions and the architecture shape; I typed every line; the method I fetched was .includes off MDN

## P1L4 - 100 words

The whole point of controlled input is to compute on each keystroke pressed by the user. The text from the input field needs to live in state. A controlled input works with two levers, value and onChange. Value points towards the state variable in which the text needs to live and onChange watches for user input (keystrokes), fires as soon as a single key is pressed, updates the state variable and react re-renders the whole app() component. When user types, onChange fires and stores that value in the declared state variable, react re-renders. As another key is pressed, onChange fires again, value in the state variable is replaced and react re-renders again.

## P1L5 - Notes

Branch naming method, locked in from today: type/short-imperative-description, kebab-case. Types: feat, fix, chore, docs, refactor, test. The test: someone reading git branch should know what merging it ships.

- I was not clear with step two instructions here:
  "Wrap the two add-inputs and button in a `<form>`, move handleAdd to onSubmit, accept the event, preventDefault line one. Acceptance test: Enter adds a transaction and the page does not reload — watch for the flash"

  So i asked :
  "Ok. i want to make sure i do the right thing as you told me. I am putting the two input fields, description and amount, inside `<form></form>`. and instead of
  `onClick={() => handleAdd()}`
  you want me to write `onSubmit ={() => handleAdd()}`?
  and what is `preventDefault`? Where do i use it?"

  `<form>` Is a browser tag. when it fires (submits), the following happens: the browser packages up the field values, sends them to a server and then navigate to a new page with a response.

  `preventDefault` tells the browser "I'm handling this myself. Do not use default action." For a submit event, the default action is that whole package-and-navigate routine. One method call switches it off, the page stays alive, React stays in charge.

## P1L5 Solo Build Notes

What the user types in amount field: Dollars (for e.g. 19.99)
What the state stores: 1999
What the amount is displayed on the screen: 19.99

I used `Math.round` to fix the 19.999 issue so it is rounded to 20.00 and is stored as 2000.

And i used `.toFixed(2)` method to display the stored cents as a string with two decimal places

## P1L5 Teach-back 100 words

Our goal in this lesson was to make sure the app takes a description and an amount, validates them, and adds a new transaction to state. The add button and the two input fields now live inside a `<form>` element. The form's `onSubmit` runs the handleAdd function. HandleAdd now checks for errors in input fields before adding any new transactions (no empty fields, no words in amount field, etc.). `Number("")` is 0, 0 is a real number so `Number.isNaN(0)` is false, which is why the empty field sailed through until i added the `.trim()` guard. `preventDefault` stops the browser's default form-submission action: the package-the-fields-and-navigate-to-a-new-page routine. The amount is being stored as integer cents, but is displayed as dollars again inside the transaction component using the `.toFixed(2)` method. $0 transactions are allowed.

## P1L6 Notes

The trap — `onClick={onDelete(id)}`, no arrow. The parentheses mean run it now. So this doesn't hand React a function; it executes `onDelete(id)` during render and hands React whatever comes back — undefined. Two things break:

- It fires on render, not on click. Every row deletes itself the instant the list draws.
- On the real click, React calls undefined — nothing, or a crash.

Created and switched to branch feat/aggregate_numbers_and_component_split
branch name changed. Read mistakes.md

added new field category into transactionProps, updated the component call inside JSX and for now handleAdd adds a new transaction with category "Uncategorized"

Created a separate function to format cents back into dollars as formatting is now repeating in more than one place.
Seed data now holds six transactions, with multiple transactions having same category. This was done to check the math behind category totals we are going to code afterwards.

Category totals should show as follows:

1. Fuel: 401.50
2. Food: 14.75
3. Maintenance: 28.00
4. Grand Total: 444.25

## P1L6 Solo Build Notes

## P1L6 Teach-back 100 words
