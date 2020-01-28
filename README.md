# Vacasa Email Workflow

A dynamic HTML email workflow for building beautiful emails that render consistently in every inbox.

## Major Packages

### heml
* Enables simple, semantic code in place of complicated HTML structure
* Enforced code structure where it matters and full control when you need it
* Effortless responsive emails means mobile users get content tailored to their screens
* Consistent rendering and better accessibility
* Error reporting on render, fix issues fast
* Extensible for the future

**[HEML](https://heml.io/)**

### Handlebars
A powerful template engine allowing the dynamic substitution of data inside of variable **`{{ expressions }}`**

**[Handlebars](https://www.npmjs.com/package/gulp-compile-handlebars)**

### Utility Packages
- **[CSS Inliner](https://www.npmjs.com/package/gulp-style-inject)**
- **[HTML Minify](https://www.npmjs.com/package/gulp-htmlmin)**
- **[Gulp String Replace](https://www.npmjs.com/package/gulp-string-replace)**

## Workflow things to note

### How to get started

- Open Master Template and run **`npm install`**
- Run **`gulp develop`** (opens preview in browser and re-renders on saved changes in **`src`** folder)

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
 
- For instances where it is useful to be able to toggle **`raw-helper`** blocks on or off wrap the content with:

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
