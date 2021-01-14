### Todo App

#### Citeria

- app menu

```js
// build & set
const mainMenu = Menu.buildFromTemplate(menuTemplate);
Menu.setApplicationMenu(mainMenu);

// shift to set default menu into menuTemplate
// bug * cant assign {} must have least one props
menuTemplate.unshift({
  label: "",
});

// using 'role' keyword to use preset menu option
    {
      role: "reload", // electron preset option by rold keyword
    }
```

- IPC connection

#### on Electron side

```js
// emit event
mainWindow.webContents.send("eventName", sendingArgs);

// listen event
ipcMain.on("todo:add", ("eventName", recieveArgs) => {
  ... doing
});


```

#### on App side

```js
// listen event
ipcRenderer.on('todo:add', ("eventName", recieveArgs) => {
  ... doing
});

//emit event
ipcRenderer.send('todo:add', value);
```

- cleanup garbage memory

```js
// ref window instance back to null;
addWindow.on("closed", () => (addWindow = null));
```
