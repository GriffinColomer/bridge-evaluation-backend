# monorepo

**For this project, we will design and implement a multichain web3 application for buying and selling tokens using a general-purpose intent protocol.**

We are doing all that so that we can explore and understand:

- Why blockchains and web3 are considered as the next computing paradigm
- How to use intents and declarative paradigm to build decentralized applications
- How to use ethers, viem and other libraries to build web3 applications
- How to use nodejs, typeorm and postgreSQL to build scalable backend

To achieve these goals, we will be focusing on the following areas:

- Intro to blockchains
- Tools, languages and packages
- Code structure, patterns and organization
- Testing
- Using external APIs

At the end, we want to expose an api that returns the best time for bridging tokens via Stargate or any reasonable bridge.

This repo has some of the code snippets you need for being able to successfully complete this project. Some of the work will be split in weeks so that you can easily follow allow and do the work needed. Here is the rough outline of how we will progress. Each week, we build on the work from the previous week. The code for week `x` is saved in the branch called `felix-week-x`

:white_check_mark: :white_check_mark: :white_check_mark: **Workshop 1**: `Introductions` - Get to know the Build Fellow and other students, ask questions about the project requirements, prepare your workspace.

https://openavenuesfoundation.sharepoint.com/:p:/r/sites/fellows/Shared%20Documents/4-%20Build%20Projects/Build%20Fellows%20Workspace/Felix%20Madutsa/BP%20-%2007,%202024%20-%20Workspace%20with%20students/Presentations/Week%201%20-%20Introductions.pptx?d=we8829585ceb14746aef0e8d4ac297c72&csf=1&web=1&e=y4GQNK

Optional Readings:

- Blockchain 101:
  - Blockchain 101 : https://www.youtube.com/watch?v=_160oMzblY8
  - What is a Blockchain https://www.youtube.com/watch?v=kHybf1aC-jE
- Tokens:
  - https://www.coinbase.com/learn/crypto-basics/what-is-a-token
  - Crypto Coin vs Token: https://www.youtube.com/watch?v=422HORNUfkU
  - How To Create a Token: https://www.youtube.com/watch?v=8N0lLN26BIE
- Token Trading:
  - Exploring the following DEXes: Uniswap ([app.uniswap.org](https://app.uniswap.org/swap))

:point_right: :point_right: :point_right: **Workshop 2**: Project setup and tools – Setup the project and get familiar with the tools being used.

Here are the tools and knowledge you need for this project.

- Nodejs
- Typescript
- Redis
- Docker
- Axios / ethers

## Tools and setup.

1. Download and install iterm to use as your terminal: https://iterm2.com/
2. Make iterm your default terminal: https://stackoverflow.com/questions/60210024/how-can-i-use-iterm-as-default-terminal-on-macos
3. Create a git account: https://github.com/
4. Download and install vscode (if you do not have it already) : https://code.visualstudio.com/
5. Setup VSCode so you can open it from the terminal: https://www.freecodecamp.org/news/how-to-open-visual-studio-code-from-your-terminal/
6. Setup Format on save for VSCode https://www.youtube.com/watch?v=ilCFoEhTyM0
7. Setup save on focus change (could not find good video or tutorial for this and we can handle it when we call)

## Understanding Github

First:

1. Make sure you have a github account
2. set up SSH for git on your machine using. The steps are explained here
   - Step 1: https://docs.github.com/en/authentication/connecting-to-github-with-ssh/generating-a-new-ssh-key-and-adding-it-to-the-ssh-agent . Skip the Generating a new SSH key for a hardware security key step as it is not relevant
   - Step 2: https://docs.github.com/en/authentication/connecting-to-github-with-ssh/adding-a-new-ssh-key-to-your-github-account

- You can also follow this video if that is better: https://www.youtube.com/watch?v=X40b9x9BFGo

Now, let’s learn more about git. For the most part, all you need to know is the following:

1. repositories
2. git clone
3. git add
4. git commit
5. git push
   Useful tutorial

- [How Git Works: Explained in 4 Minutes] https://www.youtube.com/watch?v=e9lnsKot_SQ
- [Git Tutorial For Dummies] https://www.youtube.com/watch?v=mJ-qvsxPHpY

## Step by step setup

- Install software and get familiar with technical stack
  > VSCode
  >
  > > We recomnend using VSCode for writing the code. Feel free to use other code editing and development tools you like.
  > > You can download and install VSCode from here: https://code.visualstudio.com/download
  > > Iterm
  > > Instead of using the built in terminal, download and install iterm2 terminal for a much better experience.
  > > You can download and install iterm2 from here: https://iterm2.com/downloads.html
  > > NodeJs
  > > For this project, we use NodeJs as our server for running Typescript.
  > > You can download and install NodeJS from here: https://nodejs.org/en/download
  > > Node Provider
  > > To be able to connect to any blockchain, you need to use a node provider. You should create a test account with either Alchemy, Infura or QuickNode
  > > Alchemy : https://www.alchemy.com
  > > Infura : https://www.infura.io
  > > QuickNode: https://www.quicknode.com
  > > Docker
  > > We use docker for containers for running databases
  > > You can download docker here: https://www.docker.com
- Create git repo
  > If you do not have a github account, please create one here: https://github.com
  > After that, create a new git repository for this project
  >
  > > Feel free to name the repository whatever name you prefer. I called mine bridge-evaluation-backend
  > > To learn more about how to create a github repository, follow the steps here: https://docs.github.com/en/get-started/quickstart/create-a-repo
- Start a nodejs project with TS
  > Using the github repository before, start a Typescript project using the followig steps
  >
  > > Clone the repostory you created to your local environment. Example is here: https://github.com/git-guides/git-clone

```
git clone <path to remote>
```

> cd into the project folder

```
cd <repository-name>
```

> > Create a new branch called `starting-a-project` to start creating the new project

```
git checkout -b starting-a-project
```

> create the project

```
npm init -y
```

> install typescript

```
npm install typescript --save-dev
```

> Install NodeJS types

```
npm install @types/node --save-dev
```

> create a config file `tsconfig.json`

```
npx tsc --init --rootDir src --outDir build \
--esModuleInterop --resolveJsonModule --lib es6 \
--module commonjs --allowJs true --noImplicitAny true
```

> create a src folder and add an `index.ts` file

```
mkdir src && touch src/index.ts
```

> Open the `index.ts` file and add the following print statement

```
console.log('Hello world!')
```

> verify that everything runs as expected using the following

```
npx ts-node ./src/index.ts
```

> > you should see a `'Hello world!'` output on the terminal

Congratulations, you have a working project. Let's save this project to git before we proceed.

- Make your first pull request (PR)
  > Now, we want to our code to git
  >
  > > you may need to sign in to git. You can follow the steps here if you run into issues https://docs.github.com/en/get-started/quickstart/set-up-git
  > > if/after we are signed in, let's commit and push our code

```
git commit -am "initializing the project" && git push -u origin starting-a-project
```

> after the branch has been pushed the main, lets create a new PR
>
> > follow the steps here: https://docs.github.com/en/pull-requests/collaborating-with-pull-requests/proposing-changes-to-your-work-with-pull-requests/creating-a-pull-request
> > after creating a the PR, merge it to main
> > You can follow the steps here: https://docs.github.com/en/pull-requests/collaborating-with-pull-requests/incorporating-changes-from-a-pull-request/merging-a-pull-request

- Add Redis container to the project
  > first, let's create a new branch called `adding-redis-containers`

```
git checkout main && git pull && git checkout -b adding-redis
```

TODO(felix): on the call with everyone

`Bonus`:

- Adding nodedemon to the project
  > Nodedemon enable auto reload of the server whenever the code changes. This means we do not need to manually restart the server every time we change something, thereby saving us time.
  > first, let's create a new branch called `adding-nodedemon`

```
git checkout main && git pull && git checkout -b adding-nodedemon
```

> After that, copy the provided nodemon.json file

> After that, update the package.json to including a `start:dev` script that starts nodedemon

> After that, test that nodedemon is set properly by running the following command:

```
npm run start:dev
```

> After verifying that the server is running with nodedemon, we can push our code .

```
git commit -am "adding-nodedemon" && git push -u origin adding-nodedemon
```

**Workshop 3**: Introduction to blockchains and token standards – Introduction to blockchains, tokens standards and intent protocols.

**Workshop 4**: Backend for listening to buy orders – Build the system for listening to buy orders being submitted to the protocol.

**Workshop 5**: Backend for listening to sell orders – Build the system for listening to sell orders being submitted to the protocol

**Workshop 6**: Backend for reconciling orders – Build the system for matching the orders with orders with the fill transactions.

**Workshop 7**: Backend for filling orders – Build and automated way to fill for orders based on whether it is profitable or not.

**Workshop 8**: Presentations - Polish your project deliverables and present them to the Build Fellow and other students in the final group session.
