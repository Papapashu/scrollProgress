# scrollProgress [![Build Status](https://travis-ci.org/jeremenichelli/scrollProgress.svg)](https://travis-ci.org/jeremenichelli/scrollProgress)

Small library that creates a progress bar that indicates how much you've scrolled on a website. It's very useful to show the reading progress in an article or a blog post.

### Install

After you included the script in your project or just added a script tag with the file

```html
<script src="js/scrollProgress.min.js"></script>
```

also available on **bower**

```bash
bower install scrollprogress --save-dev
```

... and **npm**

```bash
npm install scrollprogress --save-dev
```


### Use

To start tracking the scroll progress on your project you just need to call the set method and a progress bar will appear at the bottom of the page as you move inside the page.

```js
scrollProgress.set();
```

You probably want to change the appearance of the bar like its height, color or position to match your page style. Well, good news! The **set** method supports this configurable options.

```js
scrollProgress.set({
    color: '#FF9900',
    height: '12px',
    bottom: false
});
```

What if you don't like inline styles and you want to handle the look of it in your CSS style sheet, then you just need to pass a **styles** flag and set it to ```false```.

```js
scrollProgress.set({ styles: false });
```

The only thing that the script will control will be the width of the progress bar as you scroll, the rest of the styling is all on you. _Remember that the script won't put any styles at all so make sure to position the bar as fixed in your page or you won't be able to see it._


### Events inside the script

To be able to work, **scrollProgress** adds events when the window scrolls and when it gets resized to update some emtrics and keep it consistent. There's a chance that you're using these events in your page for other purposes.

To prevent overrides in these events you can pass a flag called ```events``` with a ```false``` value. Then you have to call ```scrollProgress.trigger()``` on scroll and ```scrollProgress.update()```on resize to make sure the code works as expected.

```js
scrollProgress.set({ events: false });

window.onscroll = function() {
    // some stuff you need to do on scroll
    scrollProgress.trigger();  
};

window.onresize = function() {
    // some stuff you need to do on resize
    scrollProgress.update();  
};
```

### Elements in your page

The script appends two elements with the ids **progress-wrapper** and **progress-element**, but you can change these names by adding a ```prefix``` property to the configuration object.

```js
scrollProgress.set({ prefix: 'my-awesome-page-progress-bar' });
```

Now these will be the elements added to your page.

```html
<div id="my-awesomepage-progress-bar-wrapper">
    <div id="my-awesomepage-progress-bar-element"></div>
</div>
```

### Size

This script weights 4.25KB, 1.09KB uncompressed and only 588 bytes uncompreseed and gzipped.

### Contribute

Feel free to rise an issue or suggest a change that you think that can improve this code.

