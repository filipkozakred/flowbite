---
layout: home
title: Tailwind CSS Laravel - Flowbite
description: Learn how to install and set up Tailwind CSS with Flowbite using Laravel Mix and start building modern websites with the most popular PHP framework in the world
group: getting-started
toc: true
requires_laravel: true

previous: Vue
previousLink: getting-started/vue/
next: Svelte
nextLink: getting-started/svelte/
---

Laravel is the most popular PHP web framework based on the model-view-controller (MCV) model that helps you build modern web applications and API's.

Use the officially recommended Tailwind CSS utility-first framework and the UI components from Flowbite to enhance your front-end development process.

## Install Tailwind CSS with Laravel

Make sure that you have <a href="https://getcomposer.org/" rel="nofollow">Composer</a> and <a href="https://nodejs.org/en/" rel="nofollow">Node.js</a> installed locally on your computer.

Follow the next steps to install Tailwind CSS and Flowbite with Laravel Mix. 

1. Require the Laravel Installer globally using Composer:

```bash
composer global require laravel/installer
```

Make sure to place the vendor bin directory in your PATH. Here's how you can do it based on each OS:

- macOS: `export PATH="$PATH:$HOME/.composer/vendor/bin"`
- Windows: `set PATH=%PATH%;%USERPROFILE%\AppData\Roaming\Composer\vendor\bin`
- Linux: `export PATH="~/.config/composer/vendor/bin:$PATH"`

2. Create a new project using Laravel's CLI:

```bash
laravel new awesome-project

cd awesome-project
```

You can now access the Laravel application on `http://localhost:8000`.

This command will initialize a blank Laravel project that you can get started with.

3. Install Tailwind CSS and Flowbite using NPM:

```javascript
npm install -D tailwindcss postcss autoprefixer flowbite
```

4. Create a Tailwind CSS config file:

```bash
npx tailwindcss init
```

A new `tailwind.config.js` file will be created inside your root folder.

5. Add the view paths and require Flowbite as a plugin inside `tailwind.config.js`:

```javascript
module.exports = {
    content: [
      "./resources/**/*.blade.php",
      "./resources/**/*.js",
      "./resources/**/*.vue",
      "./node_modules/flowbite/**/*.js"
    ],
    theme: {
      extend: {},
    },
    plugins: [
        require('flowbite/plugin')
    ],
  }
```

This will tell the compiler from Tailwidn what files to look for to properly apply the classes inside the final CSS file and it will also install the extra plugin options from Flowbite.

6. Add Tailwind CSS to your Laravel Mix configuration by requiring it inside the `webpack.mix.js` file:

```javascript
mix.js("resources/js/app.js", "public/js")
  .postCss("resources/css/app.css", "public/css", [

    // add here
    require("tailwindcss"),

  ]);
```

7. Add the directives inside the `./resources/css/app.css` file:

```css
@tailwind base;
@tailwind components;
@tailwind utilities;
```

8. Include the `app.css` file inside the `<head>` tag of your view templates:

```html
<link href="/css/app.css" rel="stylesheet">
```

9. Require the `flowbite.js` file before the end of the `<body>` tag:

```html
<script src="../path/to/flowbite/dist/flowbite.js"></script>
```

Alternatively, you can also include the JavaScript file using CDN:

```html
<script src="https://unpkg.com/flowbite@{{< current_version >}}/dist/flowbite.js"></script>
```

Now that you've set everything up start up a local development server using `php artisan serve` and run the build process for Webpack by using `npm run watch`.

## Flowbite components

Now that you have successfully installed the project you can start using the UI components from Flowbite and Tailwind CSS to develop modern websites and web applications.

We recommend exploring the components using the search bar navigation (`cmd` or `ctrl` + `k`) or by browsing the components section of the sidebar on the left side of this page.

<!-- ## Boilerplate Github Repository

Download or clone the Flowbite Laravel Github boilerplate repository to get access to a project that already has Laravel, Tailwind CSS, and Flowbite set up for development.

```bash
git clone ...
``` -->