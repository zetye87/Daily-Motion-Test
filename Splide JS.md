# **Installation**
---
You have 4 options to include Splide on your site.

## **NPM**

The recommended installation method is NPM. Install the latest version by the following command:

```
$ npm install @splidejs/splide
```

## **Hosting Files**
You can download the Splide package from the following link:


[Download](https://github.com/Splidejs/splide/releases/latest/)

Go to the ```dist/js``` directory, and import the ```splide.min.js``` file by the ```<script>``` tag:

```HTML  
<script src="path-to-the-file/splide.min.js"></script>
```

## **CDN**
You can also include this library from CDN:

[jsDelivr](https://www.jsdelivr.com/package/npm/@splidejs/splide?path=dist)

For production, I recommend using a specific version number instead of the "latest" keyword to avoid unexpected breakage from the further update.

## **Integration**

Integration packages are available for React, Vue and Svelte.


- [React Splide](https://splidejs.com/integration/react-splide/)
- [Vue Splide](https://splidejs.com/integration/vue-splide/)
- [Svelte Splide](https://splidejs.com/integration/svelte-splide/)


:warning: The latest version only supports **Vue 3**. You have to use the old version (0.3.5) for Vue 2, but the Splide version is also outdated.

  
# **Importing CSS**
---
Secondly, select the CSS file and link it to your site.

## **Files**
You will see several CSS files in the ```dist/css``` and ```dist/css/themes``` directories.

| File |	Description |
| --- | --- |
| ```splide.min.css``` |	Includes all styles. The content is same with ```splide-default.min.css``` |
| ```splide-[theme].min.css``` |	Includes all styles |
| ```splide-core.min.css``` |	Includes only core styles |

If you want to fully customize the slider appearance, pick the ```splide-core.min.css``` file that does not include arrows, pagination and progress bar styles, which reduces unnecessary "override" works. Otherwise, select ```splide.min.css``` or ```splide-[theme].min.css```.

Linking The Style Sheet
Once select a theme, link to the file by the ```<link>``` element.

```HTML
<!-- Link to the file hosted on your server, -->
<link rel="stylesheet" href="path-to-the-file/splide.min.css">

<!-- or link to the CDN -->
<link rel="stylesheet" href="url-to-cdn/splide.min.css">
```

# **HTML**
---
Next, write the required markup to build your slider.

## Basic Structure
This is the basic HTML structure that Splide requires:

```HTML
<div class="splide">
  <div class="splide__track">
		<ul class="splide__list">
			<li class="splide__slide">Slide 01</li>
			<li class="splide__slide">Slide 02</li>
			<li class="splide__slide">Slide 03</li>
		</ul>
  </div>
</div>
```

Insert any contents inside ```.splide__slide``` elements such as images and texts. You can use ```<div>``` element instead of ```<ul>``` and ```<li>```, but they should be a list element in terms of semantic markup.


😃 When you create an image slider, the ```cover``` option is useful. It converts all images to the ```background-image``` of each parent element. That means you don't have to crop images by your image editor.


## Additional HTML
You may need to add more HTML markups in following cases:

- Using custom arrows
- Adding a progress bar or play/pause buttons for autoplay

See [Arrows](https://splidejs.com/guides/arrows/), [Autoplay](https://splidejs.com/guides/autoplay/), or [Structure for more details](https://splidejs.com/guides/structure/).

# **Applying Splide**
---
Finally, apply Splide to your HTML element.

## Using Import
Import the ```Splide``` class, instantiate it, and call the ```mount()``` method. The first argument of the constructor accepts a **CSS selector**, or **an element** itself.

```Javascript
import Splide from '@splidejs/splide';

new Splide( '.splide' ).mount();
```

Do not forget to call ```mount()``` method, or nothing will appear in the browser.

## Using The Global Class
If you include the library via the ```<script>``` tag, you can globally access the Splide class.

```HTML
<script>
  new Splide( '.splide' ).mount();
</script>
```

Make sure **the target element is loaded** before constructing the Splide instance.

```HTML
<script>
  document.addEventListener( 'DOMContentLoaded', function() {
    var splide = new Splide( '.splide' );
    splide.mount();
  } );
</script>
```

# **Multiple Sliders**
---
Each Splide instance can create only one slider. Even if you pass a class name to the constructor, Splide applies the slider to only the first matched element. If you want to build multiple sliders, **create same number of instances** respectively.

```Javascript
new Splide( '#slider1' ).mount();

new Splide( '#slider2' ).mount();

new Splide( '#slider3' ).mount();
```

Or you can initialize them by the ```for``` loop:

```Javascript
var elms = document.getElementsByClassName( 'splide' );

for ( var i = 0; i < elms.length; i++ ) {
  new Splide( elms[ i ] ).mount();
}
```

