Took too long to begin the actual work. 2 weeks to do the pre read is not acceptable moving forward.
There's a name for what almost happened: yak shaving. It's when you sit down to do task A, realize you "should probably" do task B first, which makes you think you need to do task C, which depends on task D… and three hours later you've shaved a yak and forgotten what you came to do.
caught myself wanting to yak-shave the environment before L1. Resisted.
Don't update dependencies at the start of a session. Update them when you have a specific reason to, and never right before you're about to build something.
So when Claude asks me a question, I need to answer it with my own words instead of looking at docs or my journal entries.
Used Safari for local React dev, HMR appeared broken. Switched to Chrome and it worked. Use Chrome for dev, Safari for general browsing. That's the lesson I got from here.

1. React lets you combine markup, CSS, and JavaScript into these things called components, which you can render into your app's UI. It's basically a function sprinkled with markup. That markup is embedded into javascript using a html like syntax called JSX. A component could be as small as a button or an entire page. It could be reused anywhere you want to in your app. But why capital letters for defined components? Also why is defining components inside other components buggy and slow? I mean, if I was to use the components only once, then I could define it inside the other component. But it's good practise to define all the components up top because that way you can import those into other files.
2. React has props. You can render information from one component inside another using props. Defining props goes something like this:
   function Profile({name,age,jobTitle}). Profile is the defined component. name, age, jobTitle are the props.
3. what persists in React between renders is the current input value. React needs to remember what the user input was before it renders something new (function runs again). The mechanism is called state, and the React tool for declaring it is useState. Props get passed in fresh each render. State persists

Missing answers:

1. a React component "has" props (data coming in from outside, like constructor arguments) and state (data it manages internally, like private member variables).
2. C++: Foo myObj(arg1, arg2); — you call the constructor with positional arguments.
   React: <Foo name="Maria" age={30} /> — you "instantiate" by writing the component as a JSX tag, and you pass arguments as named attributes.
3. Props don't persist — they get handed in fresh by the parent every render. Local variables declared inside the function body don't persist — they're created from scratch each render. State is the only thing the component itself remembers.

## 2026-05-17 — Props are one object, not multiple arguments

Alright, so far we've made changes to the App.tsx file. We deleted everything that was there before, And Claude told me to add another function called greeting inside. He told me to add another prop in it called role, and I was confused between putting props. What I did was put prop name and then the name was a string, and then I put a comma and then I put role and then I put role string.

What VS code did was to help me fix it. It is actually name, role; its name is a string; role is a string.
Initial mistake was something like this.

`function Greeting({name}:{name:string},{role}:{role:string})`

The fix is this

`function Greeting({ name, role }: { name: string; role: string })`

The first curly braces block is telling what the function is receiving, and the second curly braces block tells what type of value is being received in the first block.
A React component always receives exactly one argument, an object containing all its props. All destructuring goes in one set of braces, and all types go in one set of braces.

index.html is empty because it's not the content — it's the launchpad. It contains a root div and a script tag. The script tag loads JavaScript, which builds the actual content by inserting it into the root div at runtime.

P1L1 conceptual gaps

2. Components are recognized by capitalization. `<App />` → developer-written component because of the capital A. `<div /> `→ HTML element provided by the browser because of the lowercase d. React looks only at the first character to decide. The original mistake: thinking lowercase tags came "from React's library." They don't — they're HTML, built into the browser, not React.
3. useState survives re-renders, but it cannot survive a page refresh.

4. A package.json just contains the name of the modules that the app is going to need. We don't need to upload the entire node_modules folder on GitHub. If somebody clones my repository from GitHub and runs the command `npm install`, it automatically installs all the required packages that are listed in the package.json file on the local machine of whoever cloned my repository.

Engineering habits i want to keep

5. Do not update anything while you are working inside a project. Do not update node version, npm version, or vite version while you are working inside a project. That thing only occurs before you start up the project and set up your environment.

6. For HMR debugging, always use Chrome instead of Safari. Safari has caused issues before, and I do not want to refresh pages again and again, but i don't need to do that with Chrome. Chrome also has better debugging tools.

7. Before doing a `git add.`, always do a `git status` check to see what things need to be added and what things are already added by the color red or green.

## 2026-05-27 - P1L2 Core lesson

`.map()` doesn't hand you back the original transactions. It hands you back a brand new array containing whatever your transformation rule produced for each item.

console output is signal mixed with noise, and learning to spot the difference is part of my job.

key must be unique among siblings, and stable for the lifetime of the item.
keys aren't about being numbers, they're about identity that survives change.
key is supposed to answer "which transaction is this?" not "where in the array is this?"

stored values are facts; derived values are computations. Stored has to live somewhere. Derived is produced on demand and thrown away.

## P1L5 - Mistakes in answers

- Recall question 4 was answered wrong

Question - (Standing target) You want to display how many transactions are currently visible after filtering. Stored or derived? Where does it live and why?

My Wrong Answer - This is a derived value. It lives in state because it is subject to change every time the filter produces new set of transactions. Storing a computed value will result in lag and re render will not surface it. It would require a page refresh.

Real Answer - Derived means it does not live in state. Anything that gets computed each render does not live in state. Changing across renders is not what makes somthing state. The real test: can I compute it from existing state or props? Yes → const. Is it a fact nothing else can produce — something only the user or the world knows? → state.

- One error in question 1

question: (L2) Who actually reads the key prop — and why does array index stop working as a key the moment items can be deleted?

My answer: React reads the key prop. Array index stop working as a key the moment items are deleted because every re render, the index will reset and each item will be assigned a new key. That defeats the purpose of each item having a unique identity.

Error: Indexes don't 'reset'. They 'shift'. Delete item 0 and every other item below moves up a slot. So key 1 still exists but it is now pointing at a different transaction.

- Fixed error in the following

i was asked to create a const variable counting the number of transactions. I looked up the method on MDN website and the method is `.length` so I needed to count the transactions not the `searchText` so it will not be `searchText.length`, it will be `filteredTransactions.length`

## P1L5 Mistakes in code

- I accidently wrote the guard rails inside the `const newTransaction` in the `handleAdd()` function. The correct way is to use the guard rails directly below `preventDefault` and before `const newTransaction`.

The 5 acceptance tests for guard rails to work:

1. Both fields empty, Enter → nothing added
2. Description is only spaces → nothing added
3. Description filled, amount is "abc" → nothing added
4. Description filled, amount field left empty → nothing added
5. Valid pair → adds and clears, like now

guard rails i wrote:

1. `if (Number.isNaN(Number(amount))) {return;}`
2. `if (description.trim() === "") {return;}`

Attempt 1: Failed at 4rth test. Amount got added as 0

As per claude instructions, i ran three commands inside the chrome console which were as follows

1. Number("")
2. Number.isNaN(Number(""))
3. Number(" ")

Outputs were: 0, false, 0 respectively.

So to take care of the 4rth test, i added one more guard rail: `if(Number(amount) === 0){return;}`

That took care of the 4rth test. But another problem came up. If the amount was added as 0, the transaction would not be added. So i fixed the third guard. Instead of checking for 0, i will check for empty string. So third one becomes:
`if(amount === ""){return;}`

Now amount can be left empty, nothing gets added. But now amount can be added as 0.
But one more thing went wrong. Empty spaces in the amount can be added as 0. The Number(" ") test i ran in the console was meant to catch this exact error. So i fixed this with trim(). So the third guard rail now becomes `if(amount.trim() === ""){return;}`

## P1L5 Mistakes in Solo Build

- I was looking into `parseInt` and `parseFloat` methods on MDN directly. But i decided to store dollars as integers by multiplying by 100. To display those integers as Dollars again, i tried to divide by 100 but that didn't work.
- To display cents as dollars again, i instead used `.toFixed(2)` which displays a stored number as a string with two decimal places.

## P1L6 Mistakes in Answers

- Recall Questions:

1. I want to show a grand total of all transaction amounts at the bottom of the list. Should that total live in state (a fourth useState), or somewhere else? Give me the answer and the reason — and tell me specifically what breaks if you store it.

My Answer: No, it does not need to live in state. It is a derived value so it can be assigned to a const variable. If it was a factual value, something only the user or the world knows, then it needed to live in state. If we do store this in state, nothing will break.

Fix in my answer: It will break in a specific way. We store the total — `const [total, setTotal] = useState(0)`. The user deletes a transaction. Our handleDelete runs `setTransactions(filtered)` and returns. On screen right now, what number does the user see for the total, and why? Then: what would we have to bolt onto `handleDelete`, `handleAdd`, and `handleClearAll` to stop that from happening?

2. In your current code, the parent passes the delete handler down as `onDelete={handleDelete}` — a bare reference. But inside the row, the button is wired as `onClick={() => onDelete(id)}` — wrapped in an arrow function. Why the wrapper in one spot and the bare name in the other? What would go wrong if you wrote `onClick={onDelete(id)}` instead?

My Answer: I do not remember this. It was explained to me but i forgot.

Real Answer: When we wrote `onDelete={handleDelete}`, we are not calling the function, we are just passing it down as a prop to the child. When we wrote `onClick={() => onDelete(id)}`, we wrap it in a arrow function because we need to pass id, and only the child knows which one. A bare `onDelete` can't carry that. When React fires it, React calls `onDelete(event)`, handing it the click event as the id. Garbage. So we write a tiny new function, `() => onDelete(id)`, that when React calls it on click turns around and calls onDelete with the specific id we want.

- Git branch renamed to kebab-case from snake-case. It is now feat/aggregate-numbers-and-component-split

- Auto detect categories does not work until we use an LLM which comes at P5 not in P1L6. So for now, every new catogory added will be "Uncategorized"

## P1L6 Mistakes in code

## P1L6 Mistakes in Solo Build
