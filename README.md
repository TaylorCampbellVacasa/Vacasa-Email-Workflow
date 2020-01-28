# Vacasa Email Workflow

A HTML templating workflow for building beautiful, dynamic emails that render in every inbox.



Major Packages:

- [CSS Inliner](https://www.npmjs.com/package/gulp-style-inject)
- [Handlebars](https://www.npmjs.com/package/gulp-compile-handlebars)
- [HEML](https://heml.io/)
- [HTML Minify](https://www.npmjs.com/package/gulp-htmlmin)
- [Gulp String Replace](https://www.npmjs.com/package/gulp-string-replace)

## Workflow things to note

### How to get started

- Open Master Template and run **`npm install`**
- Run **`gulp develop`** (opens preview in browser and rerenders on save changes in **`src`** folder)

### Where to make changes

- Primary html source: **`src/pages/email.html`**
- Local partials, CSS, and Handlebars Data: **`src/...`**

### How to inject a new CSS file

- The css injector looks for contextual comments in the following format:

   ```html
	 <!-- inject-style src="src/CSS/YOUR_FILENAME.css" -->
	 ```

### How to selectively render Handlebars expressions

- Surround elements with **`raw-helper`** blocks to escape HEML interpolation
   ```handlebars
   {{{{raw-helper}}}} 
   <div>
	   <p>Hello, I am {{ your_expression }}</p>
   </div> 
   {{{{/raw-helper}}}}
   ```
 
- For instanses where it is useful to be able to toggle **`raw-helper`** blocks on or off wrap the content with:

  ```handlebars
	<!-- raw-helper --> ... <!-- /raw-helper -->
	```

  Then you can run **`gulp template`** to activate the blocks:

  ```handlebars
	<!-- {{{{ raw-helper }}}} --> ... <!-- {{{{ /raw-helper }}}} -->
	```

  And run **`gulp design`** to deactivate them:

  ```handlebars
	<!-- raw-helper --> ... <!-- /raw-helper -->
	```
