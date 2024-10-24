#  Lecture notes,Bootstrap Customization with Sass

## This project demonstrates how to customize Bootstrap using Sass. It includes setting up a development environment, customizing styles, compiling Sass to CSS, and configuring breakpoints and other variables.

### Prerequisites
- Node.js installed on your system.
- Basic understanding of Bootstrap, Sass, and npm.

### Getting Started
<details>
  <summary><strong>Click to read more</strong></summary>

1. **Initialize the Project** 
Begin by setting up a new Node.js project and installing Bootstrap:

```bash 
    npm init -y
    npm install bootstrap
```


2.	**Project Structure**
Create the following folder structure:
project-root/
├── node_modules/
├── scss/
│   └── custom.scss
├── css/
├── index.html
├── package.json

3.	**Configuring Sass and Bootstrap**
- Import Bootstrap’s SCSS file in scss/custom.scss:
```scss
// scss/custom.scss
@import "../node_modules/bootstrap/scss/bootstrap";
•	You can override Bootstrap’s default variables above the import:
$primary: #3498db; // Custom primary color

@import "../node_modules/bootstrap/scss/bootstrap";
```

4.	**Customizing Breakpoints**
You can add custom breakpoints using map-merge():
```scss
$new-breakpoints: (
    xl: 1280px,
    xxl: 1600px
);

$grid-breakpoints: map-merge($grid-breakpoints, $new-breakpoints);

// Re-import Bootstrap to apply changes
@import "../node_modules/bootstrap/scss/bootstrap";
```
5.	**Compiling Sass** 
Set up a script in package.json to compile Sass into CSS:
```json
"scripts": {
    "watch": "sass --watch scss/custom.scss:css/style.css",
    "build": "sass scss/custom.scss:css/style.css --style compressed"
}
```
- Run the watch script to automatically compile changes:
```bash 
npm run watch
```

- For a production build with minified CSS:
```bash 
    npm run build
```
Using Custom CSS in index.html

Create an index.html file that references the compiled CSS: 
```html  
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <link rel="stylesheet" href="css/style.css">
    <title>Bootstrap Customization</title>
</head>
<body>
    <main class="container">
        <div class="grid">
            <div class="g-col-6">Column 1</div>
            <div class="g-col-6">Column 2</div>
        </div>
    </main>
</body>
</html>
```
</details>


### Configuring CSS Grid
<details>
  <summary><strong>Click to read more</strong></summary>

Bootstrap has an optional CSS grid system. Enable it by setting the variable and using grid-specific classes:

1.	**Enable CSS Grid**
```scss
    $enable-cssgrid: true;
    @import "../node_modules/bootstrap/scss/bootstrap";
```   


2.	**Use CSS Grid in HTML**
Replace .row and .col-* with .grid and .g-col-*:
```html
<div class="grid">
    <div class="g-col-6">Column 1</div>
    <div class="g-col-6">Column 2</div>
</div>
```
</details>

### Troubleshooting Warnings
<details>
  <summary><strong>Click to read more</strong></summary>

Older versions of Bootstrap may produce warnings due to stricter SCSS rules. Use a compatible version to avoid these warnings:
```bash 
npm install bootstrap@5.3.3 --save-exact
```
</details>

### Additional Notes
<details>
  <summary><strong>Click to read more</strong></summary>

- Source Maps: The .map file generated during compilation helps in debugging by mapping the compiled CSS back to the original SCSS source.
- Breakpoints and Containers: Override only the necessary variables using map-merge() to avoid overriding the entire configuration.
</details>

### Features
<details>
  <summary><strong>Click to read more</strong></summary>
	•	Custom Color Scheme: Override default Bootstrap colors with your own.
	•	Responsive Design Tweaks: Easily customize grid breakpoints and container widths.
	•	CSS Grid Support: Enable Bootstrap’s experimental CSS grid feature.
	•	Build Scripts: Automate CSS generation with npm scripts for development and production.
    </details>
