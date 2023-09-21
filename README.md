# Monorepo node

- Create a react client web app
- Create a server express backend app
- handle all using the parent project

start client and server
```bash
yarn start
```

## create parent project

install yarn
```bash
npm install --global yarn
```
init the project, to create the `package.json`
```bash
yarn init -y
```

### setup workspaces

open the `package.json` and setup the `workspaces`, and setup `private` as true

```txt
  "private": true,
  "workspaces": ["client", "server"]
```
![setup-workspaces.jpg](_img%2Fsetup-workspaces.jpg)

### setup concurrently

```bash
yarn add concurrently -D -W

# start client and server
yarn start
```

![add-concurrently.jpg](_img%2Fadd-concurrently.jpg)

## create client project

from the parent folder
```bash
npx create-react-app client
```

setup `proxy` in order to use the server and client in the same origin.
The server is running in the port 3200

```txt
  "proxy": "http://localhost: 3200",
```

from the parent folder,
```bash
# install dependency
yarn workspace client start
```

## create server project

from the parent folder
```bash
mkdir server && cd server && yarn init -y
```
from the parent folder, lets go to install `express` dependency into the `server` project
```bash
# install dependency
yarn workspace server add express

# to hot reload servers
yarn workspace server add nodemon -D
```
from the server folder, create the index.js file to setup the server
```bash
touch index.js
```

from the parent folder, 
```bash
# install dependency
yarn workspace server start
```

setup the `package.json`

```txt
  "scripts": {
    "start": "nodemon index.js"
  },
```

