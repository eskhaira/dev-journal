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

2. Components are recognized by capitalization. `<App />` → developer-written component because of the capital A. `<div /> `→ HTML element provided by the browser because of the lowercase d. React looks only at the first character to decide. The original mistake: thinking lowercase tags came "from React's library." They don't — they're HTML, built into the browser, not React.
3. Use state survives re-renders, but it cannot survive a page refresh.

4. A package.json just contains the name of the modules that the app is going to need. We don't need to upload the entire node_modules folder on GitHub. If somebody clones my repository from GitHub and runs the command `npm install`, it automatically installs all the required packages that are listed in the package.json file on the local machine of whoever cloned my repository.

Engineering habits i want to keep

5. Do not update anything while you are working inside a project. Do not update node version, npm version, or vite version while you are working inside a project. That thing only occurs before you start up the project and set up your environment.

6. For HMR debugging, always use Chrome instead of Safari. Safari has caused issues before, and I do not want to refresh pages again and again, but you don't need to do that with Chrome. Chrome also has better debugging tools.

7. Before doing a `git add.`, always do a `git status` check to see what things need to be added and what things are already added by the color red or green.
