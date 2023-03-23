# blogpost1
The purpose for this blog is to better understand file structure in a sveltekit application. SvelteKit is different from a basic HTML, CSS, Javascript application, the file structure is a little more complicated, but in the end saves a lot of time setting up your application to allow you more time for creativity in your application.

## File Structure Overview
For most SvelteKit applications, the basic file structure will look like this:
```
my-project/
├ src/
│ ├ lib/
│ │ ├ server/
│ │ │ └ [your server-only lib files]
│ │ └ [your lib files]
│ ├ params/
│ │ └ [your param matchers]
│ ├ routes/
│ │ └ [your routes]
│ ├ app.html
│ ├ error.html
│ ├ hooks.client.js
│ └ hooks.server.js
├ static/
│ └ [your static assets]
├ tests/
│ └ [your tests]
├ package.json
├ svelte.config.js
├ tsconfig.json
└ vite.config.js
```
Inside this hierarchy structure the project has seven top level items. A src folder,tests folder, package.json file, svelte.config.js file, tsconfig.json file, and a vite.config.js file. The src folder is going to contain most of your files and will have multiple hierarchy levels inside of it. The other folders will simply contain files and for the most part not have any smaller folders inside of them. 
I will go through each part of this file structure and will explain what type of files go in each folder and what their functions are in the project as a whole.

### scr
```
├ src/
│ ├ lib/
│ │ ├ server/
│ │ │ └ [your server-only lib files]
│ │ └ [your lib files]
│ ├ params/
│ │ └ [your param matchers]
│ ├ routes/
│ │ └ [your routes]
│ ├ app.html
│ ├ error.html
│ ├ hooks.client.js
│ └ hooks.server.js
```
The src folder contains most of your project. This folder will look different based on the project you are working on, but some things will be in every project you do. Every project will have a ```src/routes``` and ```src/app.html``` endpoints. 

#### ```src/lib``` 
This contains your libary code which consists of utilities and components. These can be imported using the ```$lib``` alias, or can be packaged up using ```svelte-package```. 

##### ```src/lib/server```
This folder in the lib folder contains server-only library code. It can be imported by using the ```$lib/server``` alias. SvelteKit will not allow you to import these in client code. 

#### ```src/params```
This folder contains any param matchers for your project that you need. 

#### ```src/routes```
This folder contains most of your code that you will write. You create routes that you want like ```/about``` or ```/posts``` and you can add a ```/[slug]``` folder to a route to create a route with a parameter that can be used to load data dynamically when a user requests a page. 
A ```+page.svelte``` file goes into an endpoint folder. This file defines a page of your app. Along with this svelte file you can also add a ```+page.server.js``` file to add functions to your page. This can fetch data from a database that you can use on your page. 

#### ```app.html```
This file is your page template which looks like the following. This contains the elements needed by the app plus andy markup for a rendered page. All together this file allows you to work with SvelteKit and access all its functions.
```
<!DOCTYPE html>
<html lang="en">
	<head>
		<meta charset="utf-8" />
		<link rel="icon" href="%sveltekit.assets%/favicon.png" />
		<meta name="viewport" content="width=device-width" />
		%sveltekit.head%
	</head>
	<body data-sveltekit-preload-data="hover">
		<div>%sveltekit.body%</div>
	</body>
</html>
```

#### ```error.html```
This is the page that is rendered when everything else fails. Here you can add an error message that will appear if something fails in your code. This is good so that you can control what happens in your project even when something goes wrong. 

### static
```
├ static/
│ └ [your static assets]
```
In this folder goes static assests, these are assets that will not change. These can be images or text files that you may want to use in your project, but do not need to be dynamic. Pictures and text that you want to be able to plug into your endpoints can be put in this folder and can be used by mapping to this directory.

### Other Files
```
├ tests/
│ └ [your tests]
├ package.json
├ svelte.config.js
├ tsconfig.json
└ vite.config.js
```

#### ```/tests```
This is an optional folder that is only used if you added Playwright for browser testing when you set up your project, the tests will be put in this directory. 

#### ```package.json```
This endoint is created when you run ```npm create svelte@latest``` in the terminal. This file records important metadata about a project which is required before publishing to NPM. Here is an example file. 
```
{
	"name": "eg-routes",
	"version": "0.0.1",
	"private": true,
	"scripts": {
		"dev": "vite dev",
		"build": "vite build",
		"preview": "vite preview"
	},
	"devDependencies": {
		"@sveltejs/adapter-auto": "^2.0.0",
		"@sveltejs/kit": "^1.5.0",
		"svelte": "^3.54.0",
		"vite": "^4.0.0"
	},
	"type": "module",
	"dependencies": {
		"simpledotcss": "^2.1.1"
	}
}
```

#### ```svelte.config.js```
This file contains your Svelte and SvelteKit configuration. This is what an example file looks like.
```
import adapter from '@sveltejs/adapter-auto';

/** @type {import('@sveltejs/kit').Config} */
const config = {
	kit: {
		// adapter-auto only supports some environments, see https://kit.svelte.dev/docs/adapter-auto for a list.
		// If your environment is not supported or you settled on a specific environment, switch out the adapter.
		// See https://kit.svelte.dev/docs/adapters for more information about adapters.
		adapter: adapter()
	}
};

export default config;
```

#### ```vite.config.js```
A SvelteKit project is really just a Vite project that uses the ```@sveltejs/kit/vite``` plugin with any other Vite configuration. 
```
import { sveltekit } from '@sveltejs/kit/vite';
import { defineConfig } from 'vite';

export default defineConfig({
	plugins: [sveltekit()]
});
```

## Conclusion
SvelteKit has a very unique file structure that is unlike other front-end applications. It has many positives and negatives and a format that works well for some projects. This file structure may look complex at first, but it actually is rather simple and makes finding everything very easy and keeps all your different files organized. 

The lib folder holds all your libraries that you need for your project. The src is the main file folder for most of your code and is the directory that you will deal with the most. Within that, the routes directery will act as your pages for your project. The static folder holds all your images and text files you want to use in your project that does not need to be dynamic at all. The rest of the folders and files have their function, but you will not have to deal with them much throughout your project. 

I hope this blog helped you better understand the file structure of a SvelteKit project and the functionality of this system.
