# How to Setup Tailwind CSS in your Vanilla HTML Project

https://nachoiacovino.com/blog/how-to-setup-tailwind-css-in-a-vanilla-html-project

https://github.com/nachoiacovino/next-tailwind-portfolio/blob/master/data/blog/how-to-setup-tailwind-css-in-a-vanilla-html-project.mdx

![image](https://user-images.githubusercontent.com/3156358/148619911-e9e9441c-023d-4112-859a-f4580f257e0a.png)

title: How to Setup Tailwind CSS in your Vanilla HTML Project  
date: '2021-08-04'  
tags: ['tailwind css', 'html', 'tutorial']  
draft: false  
summary: 'Easiest way to setup Tailwind CSS in your Vanilla HTML project. Quick and easy   step-by-step guide.'  


## Introduction

In this tutorial, I'm gonna explain how to setup Tailwind in the easiest way possible into your static HTML project.

## Required tools

We are gonna need Node.js for this tutorial, if you don't have it, you can download it [here](https://nodejs.org/en/).

You should get the "Recommended" version.

## Installation

Create a folder for your project, open a terminal inside and do

```bash
npm init -y
npm install -D tailwindcss autoprefixer
```

With this, you initialize a new node project (the -y flag is to say yes to all prompts automatically) and install the required dependencies, in this case, Tailwind CSS and Autoprefixer, which is a dependency of Tailwind itself.

After that, we're gonna create a new folder called `src` and add a new file called `tailwind.css` inside of it.

Then, we'll add these three lines to the file.

```css
@tailwind base;
@tailwind components;
@tailwind utilities;
```

Then, we need to add a couple of scripts to our `package.json`, `dev` and `build`.

```js {7-8} showLineNumbers
{
  "name": "tailwind-css-in-vanilla-html",
  "version": "1.0.0",
  "description": "",
  "main": "index.js",
  "scripts": {
    "dev": "tailwindcss build -i ./src/tailwind.css -o ./public/tailwind.css",
    "build": "NODE_ENV=production npm run dev",
    "test": "echo \"Error: no test specified\" && exit 1"
  },
  "keywords": [],
  "author": "",
  "license": "ISC",
  "devDependencies": {
    "autoprefixer": "^10.3.1",
    "tailwindcss": "^2.2.7"
  }
}
```

Let's explain what's going on here, in the `dev` script, we're calling tailwindcss to build, and we're giving it an input file with -i, the `.src/tailwind.css` we just created in the previous step. Then, we're giving it an output file with -o, and that's gonna be `.public/tailwind.css`, which would be all Tailwind CSS classes after the build process.

In the `build` script, we're calling the `dev` but with `NODE_ENV=production` in front of it, we're gonna use this to create an optimized version of our Tailwind CSS file with only the classes we need for our project.

We can now run this command to generate the Tailwind CSS file in development mode, which will include all classes that Tailwind has available.

```bash
npm run dev
```

This also creates a `public` folder for us. Now let's create an `index.html` file inside that same folder.

Inside, add the following code:

```html {8} showLineNumbers
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <meta http-equiv="X-UA-Compatible" content="IE=edge" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>Tailwind CSS in Vanilla HTML!</title>
    <link rel="stylesheet" href="tailwind.css" />
  </head>
  <body>
    <div class="text-blue-600">hello!</div>
  </body>
</html>
```

This is a basic HTML structure but take important notice on line 8, where we're linking our `tailwind.css` file, it's important to realize this file is the one inside `public`, and not the one inside `src`.

So we can customize Tailwind a little bit better, we need to create a `tailwind.config.js`, we can do it automatically with this command:

```bash
npx tailwindcss init
```

And then, to know exactly which files Tailwind need to look at to create an optimized version of the output in the build process, we need to tell it where to look. Go to `tailwind.config.js` and modify the `purge` line.

```js {2}
module.exports = {
  purge: ['./public/**/*.html'],
  darkMode: false, // or 'media' or 'class'
  theme: {
    extend: {},
  },
  variants: {
    extend: {},
  },
  plugins: [],
};
```

And with this, you're set! You have successfully setup Tailwind CSS in your project and you're ready to create your amazing app.

If you have enjoyed this tutorial and you would like to learn more, I'm creating a Tailwind CSS course called Windcourse, in which I have a video of this exact process and I'll be also going deep into how to use Tailwind with React and Next.js.

If you are interested, [you can pre-order it here](https://app.slip.so/presale/windcourse).

Feel free to follow me on Twitter for daily tech-related content [@nachoiacovino](https://twitter.com/nachoiacovino).