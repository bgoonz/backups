# Setup - Create a Next.js App | Learn Next.js

[https://nextjs.org/learn/basics/create-nextjs-app/setup](https://nextjs.org/learn/basics/create-nextjs-app/setup)

![learn-twitter.png](Setup%20-%20Cr%20668d3/learn-twitter.png)

## Setup

First, let's make sure that your development environment is ready.

- If you don't have **Node.js** installed, [install it from here](https://nodejs.org/en/). You'll need Node.js version **10.13** or later.
- You'll be using your own text editor and terminal app for this tutorial.

> If you are on Windows, we recommend downloading Git for Windows and use Git Bash that comes with it, which supports the UNIX-specific commands in this tutorial. Windows Subsystem for Linux (WSL) is another option.
> 

### Create a Next.js app

To create a Next.js app, open your terminal, `cd` into the directory you'd like to create the app in, and run the following command:

```
npx create-next-app nextjs-blog --use-npm --example "https://github.com/vercel/next-learn/tree/master/basics/learn-starter"

```

> Under the hood, this uses the tool called create-next-app, which bootstraps a Next.js app for you. It uses this template through the --example flag.
> 
> 
> If it doesn't work, please take a look at [this page](https://github.com/vercel/next-learn/blob/master/basics/errors/install.md).
> 

### Run the development server

You now have a new directory called `nextjs-blog`. Let's `cd` into it:

```
cd nextjs-blog

```

Then, run the following command:

```
npm run dev

```

This starts your Next.js app's "development server" (more on this later) on port **3000**.

Let's check to see if it's working. Open [http://localhost:3000](http://localhost:3000/) from your browser.

**Quick Review**: What text do you see on the page?
