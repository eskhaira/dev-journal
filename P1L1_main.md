This file will hold all my journal entries for Project One, Lesson One, the coding part and the server setup and machine setup.
So before we began this, We touched up our knowledge on `useState` and how it also resets to the initial value if you refresh the page. If you wanted to store that value, we would need something called `localStorage`, which we will learn in future lessons.
Then we checked git version, node version, and npm version. Everything was up to date.
After that, we ran a command called `npm install vite@latest`. We created a project called Finance Tracker and we CD'd into it
After the install, we went into the files, and the first file we looked at was Index.html I had a doubt. why the script element was not nested inside the div element?
Answer: In HTML, the order of tags determines the order of execution. Code further down the file runs after code earlier in the file. A script tag can reach back and touch anything that came before it in the file, because those things already exist in the DOM by the time the script runs.
So when we write import something inside curly braces, that would pick a specifically named export, but when we write it without any braces, that's the default export and you can name it whatever you want. For example, in the main.tsx file, the strict mode was inside curly braces. It was asking for a specific export, but the app was in no braces, so it was asking for the default export from that file. Also, when we write `import` something from what comes after the `from`, if it starts with a dot, it means it's looking for something inside the current directory. If it starts with something, let's say `react`, no dots, no slashes, it's looking for something inside `node_modules/` for a package called `react`.
When we write `import` and then just simply write `/CSS file` or whatever the name of the CSS file is in the current directory, it just means we are not importing any function or anything. We are just asking React to include the CSS inside this page.
This specific point refers to the main.tsx file. The createRoot says that this is the DOM element where my app is going to live. document.getElementById is finding the root div inside the DOM. Then it creates a react root, which is attached to that div element, and it renders the app component inside it. The strict mode component is a development-only wrapper. When you build the app for deployment, strict mode will do nothing. While developing, it intentionally runs your components twice on every render to surface bugs you will otherwise miss. You'll occasionally see things appear to run twice in dev. That's not a bug; that is strict mode doing its job.

## 2026-05-17 — Props are one object, not multiple arguments

Alright, so far we've made changes to the App.tsx file. We deleted everything that was there before, And Claude told me to add another function called greeting inside. He told me to add another prop in it called role, and I was confused between putting props. What I did was put prop name and then the name was a string, and then I put a comma and then I put role and then I put role string.

What VS code did was to help me fix it. It is actually name, role; its name is a string; role is a string.
Initial mistake was something like this.

function Greeting({name}:{name:string},{role}:{role:string})

The fix is this

function Greeting({ name, role }: { name: string; role: string })

The first curly braces block is telling what the function is receiving, and the second curly braces block tells what type of value is being received in the first block.
A React component always receives exactly one argument, an object containing all its props. All destructuring goes in one set of braces, and all types go in one set of braces.

index.html is empty because it's not the content — it's the launchpad. It contains a root div and a script tag. The script tag loads JavaScript, which builds the actual content by inserting it into the root div at runtime.

P1L1 conceptual gaps

Candidate 2 — Components are recognized by capitalization, not by what library they come from. From today's pop quiz. The gap: thinking lowercase tags like `<div>` come from React's library. They don't — they're HTML, provided by the browser. React just looks at the first letter to decide whether to treat a tag as a component or as HTML.
Candidate 3 — useState survives re-renders but not refreshes. From the very start of today's session. You initially said it survived refreshes. This is a foundational distinction worth writing down.
Candidate 4 — package.json is a shopping list, not application code. From the quiz just now. The model of dependency-manifest-vs-installed-deps is universal across languages; worth a permanent entry.

Engineering habits i want to keep

Candidate 5 — Yak-shaving the environment. When you wanted to update Node/npm at the start of the session. The lesson: when your environment works, don't fix it. Update with intent, never mid-task. You caught yourself; worth a positive-note entry.
Candidate 6 — Use Chrome for React dev, not Safari. From the HMR debugging episode. Worth noting as a tool-defaults entry.
Candidate 7 — git status before git add, always. From the Git chunk. The discipline of reading what you're about to stage before staging it.
