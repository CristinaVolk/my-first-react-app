***How to setup a fullstack app:***
Required tools:

NodeJS
npm or yarn
In order to install Node and npm please use NVM.

[Here is the guide](https://www.freecodecamp.org/news/node-version-manager-nvm-install-guide/) hot to set up NVM:


1. Then go inside the folder `server`:
    - run the command `npm init -y` (the `package.json` will be created)
    - create a file `index.js` in the root of dir server
    - go to the `package.json` and check the prop `main`. It should point to your root file which is `index.js`
    - copy the code from the `index.sample.md` and paste it in the `index.js`
    - you will need to install the package `express` - run the command `npm install express` inside the dir `server`
    - go to the `package.json` , find the prop `"scripts"` , remove the whole line with `"test"` prop.
    - instead of `"test"` add `"start": "node index.js"`,
    - run the command `npm run start`, it will execute `node index.js`
    - you will face the error `SyntaxError: Cannot use import statement outside a module`
    - to fix it, simply add one more property to your `package.json`: `"type": "module"` just under the `"main": "index.js"`
    - run the start command again and look at your console :)
    - you can stop the server for now

2. Head to the root folder `my-first-react-app` now and stop the server for now
   - just run the command `npm create vite@latest`
     - (if this command is not working then run `npx create-react-app .`). the dot means you want to create a react project inside the existing one `client`
   - choose the project name `client`, framework: `React`, variant: `Javascript`
   - after the installation follow the instructions in the console ;)

Now you ve got 2 independent apps. One is the server (backend), the other is client(frontend). You can observe the running app in the browser. Now the question is how to connect then?
Basically, you want to query your server and get some data and display it in the browser:

1. Stop your client and server. Go to the `server/index.js` and add the following code:

```
    import cors from "cors"
    
    app.use(cors())
    
    app.get('/pokemon', async(req, res) => {
    const id = 35
    const response = await fetch(`https://pokeapi.co/api/v2/pokemon/${id}/`)
    const data = await response.json()
    console.log(data)
    
    res.json({data: data});
    });
```

2. Install `cors` with the command: `npm install cors`
3. Go to the client folder, find the `App.jsx` file and remove everything.
4. Find the `App.sample.md` copy everything and paste into the `App.jsx`
5. Start your server first by going to the folder server and hitting `npm run start`
6. Start your client inside the dir client and hitting the command `npm run dev`

Hopefully it is working!!!

Good luck :)

Obviously, message me if you are stuck, Adam!!!