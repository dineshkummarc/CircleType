# CircleType

[![Build Status](https://travis-ci.org/peterhry/CircleType.svg?branch=master)](https://travis-ci.org/peterhry/CircleType)

A JavaScript library that lets you curve type on the web.

Demo: <https://circletype.labwire.ca>

## Installation

In a browser:
```html
<script src="circletype.min.js"></script>
```

Using CDN:
```html
<script src="https://cdn.jsdelivr.net/gh/peterhry/CircleType@2.3.1/dist/circletype.min.js"></script>
```

Using npm:

```shell
$ npm i circletype --save
```

Load ES module:
```js
import CircleType from `circletype`;
```

# API

<a name="CircleType"></a>

## CircleType
A CircleType instance creates a circular text element.

**Kind**: global class  

* [CircleType](#CircleType)
    * [new CircleType(elem, [splitter])](#new_CircleType_new)
    * [.radius(value)](#CircleType+radius) ⇒ [<code>CircleType</code>](#CircleType)
    * [.radius()](#CircleType+radius) ⇒ <code>number</code>
    * [.dir(value)](#CircleType+dir) ⇒ [<code>CircleType</code>](#CircleType)
    * [.dir()](#CircleType+dir) ⇒ <code>number</code>
    * [.forceWidth(value)](#CircleType+forceWidth) ⇒ [<code>CircleType</code>](#CircleType)
    * [.forceWidth()](#CircleType+forceWidth) ⇒ <code>boolean</code>
    * [.forceHeight(value)](#CircleType+forceHeight) ⇒ [<code>CircleType</code>](#CircleType)
    * [.forceHeight()](#CircleType+forceHeight) ⇒ <code>boolean</code>
    * [.refresh()](#CircleType+refresh) ⇒ [<code>CircleType</code>](#CircleType)
    * [.destroy()](#CircleType+destroy) ⇒ [<code>CircleType</code>](#CircleType)

<a name="new_CircleType_new"></a>

### new CircleType(elem, [splitter])

| Param | Type | Description |
| --- | --- | --- |
| elem | <code>HTMLElement</code> | A target HTML element. |
| [splitter] | <code>function</code> | An optional function used to split the element's                              text content into individual characters |

**Example**  
```js
// Instantiate `CircleType` with an HTML element.
const circleType = new CircleType(document.getElementById('myElement'));

// Set the text radius and direction. Note: setter methods are chainable.
circleType.radius(200).dir(-1);

// Provide your own splitter function to handle emojis
// @see https://github.com/orling/grapheme-splitter
const splitter = new GraphemeSplitter()
new CircleType(
  document.getElementById('myElement'),
  splitter.splitGraphemes.bind(splitter)
);
```
<a name="CircleType+radius"></a>

### circleType.radius(value) ⇒ [<code>CircleType</code>](#CircleType)
Sets the desired text radius. The minimum radius is the radius required
for the text to form a complete circle. If `value` is less than the minimum
radius, the minimum radius is used.

**Kind**: instance method of [<code>CircleType</code>](#CircleType)  
**Returns**: [<code>CircleType</code>](#CircleType) - The current instance.  

| Param | Type | Description |
| --- | --- | --- |
| value | <code>number</code> | A new text radius in pixels. |

**Example**  
```js
const circleType = new CircleType(document.getElementById('myElement'));

// Set the radius to 150 pixels.
circleType.radius(150);
```
<a name="CircleType+radius"></a>

### circleType.radius() ⇒ <code>number</code>
Gets the text radius in pixels. The default radius is the radius required
for the text to form a complete circle.

**Kind**: instance method of [<code>CircleType</code>](#CircleType)  
**Returns**: <code>number</code> - The current text radius.  
**Example**  
```js
const circleType = new CircleType(document.getElementById('myElement'));

circleType.radius();
//=> 150
```
<a name="CircleType+dir"></a>

### circleType.dir(value) ⇒ [<code>CircleType</code>](#CircleType)
Sets the text direction. `1` is clockwise, `-1` is counter-clockwise.

**Kind**: instance method of [<code>CircleType</code>](#CircleType)  
**Returns**: [<code>CircleType</code>](#CircleType) - The current instance.  

| Param | Type | Description |
| --- | --- | --- |
| value | <code>number</code> | A new text direction. |

**Example**  
```js
const circleType = new CircleType(document.getElementById('myElement'));

// Set the direction to counter-clockwise.
circleType.dir(-1);

// Set the direction to clockwise.
circleType.dir(1);
```
<a name="CircleType+dir"></a>

### circleType.dir() ⇒ <code>number</code>
Gets the text direction. `1` is clockwise, `-1` is counter-clockwise.

**Kind**: instance method of [<code>CircleType</code>](#CircleType)  
**Returns**: <code>number</code> - The current text radius.  
**Example**  
```js
const circleType = new CircleType(document.getElementById('myElement'));

circleType.dir();
//=> 1 (clockwise)
```
<a name="CircleType+forceWidth"></a>

### circleType.forceWidth(value) ⇒ [<code>CircleType</code>](#CircleType)
Sets the `forceWidth` option. If `true` the width of the arc is calculated
and applied to the element as an inline style.

**Kind**: instance method of [<code>CircleType</code>](#CircleType)  
**Returns**: [<code>CircleType</code>](#CircleType) - The current instance.  

| Param | Type | Description |
| --- | --- | --- |
| value | <code>boolean</code> | `true` if the width should be set |

**Example**  
```js
const circleType = new CircleType(document.getElementById('myElement'));

circleType.radius(384);

console.log(circleType.container);
//=> <div style="position: relative; height: 3.18275em;">...</div>

// Enable the force width option
circleType.forceWidth(true);

console.log(circleType.container);
//=> <div style="position: relative; height: 3.18275em; width: 12.7473em;">...</div>
```
<a name="CircleType+forceWidth"></a>

### circleType.forceWidth() ⇒ <code>boolean</code>
Gets the `forceWidth` option. If `true` the width of the arc is calculated
and applied to the element as an inline style. Defaults to `false`.

**Kind**: instance method of [<code>CircleType</code>](#CircleType)  
**Returns**: <code>boolean</code> - The current `forceWidth` value  
**Example**  
```js
const circleType = new CircleType(document.getElementById('myElement'));

circleType.forceWidth();
//=> false
```
<a name="CircleType+forceHeight"></a>

### circleType.forceHeight(value) ⇒ [<code>CircleType</code>](#CircleType)
Sets the `forceHeight` option. If `true` the height of the arc is calculated
and applied to the element as an inline style.

**Kind**: instance method of [<code>CircleType</code>](#CircleType)  
**Returns**: [<code>CircleType</code>](#CircleType) - The current instance.  

| Param | Type | Description |
| --- | --- | --- |
| value | <code>boolean</code> | `true` if the height should be set |

**Example**  
```js
const circleType = new CircleType(document.getElementById('myElement'));

circleType.radius(384);

console.log(circleType.container);
//=> <div style="position: relative; height: 3.18275em;">...</div>

// Disable the force height option
circleType.forceHeight(false);

console.log(circleType.container);
//=> <div style="position: relative;">...</div>
```
<a name="CircleType+forceHeight"></a>

### circleType.forceHeight() ⇒ <code>boolean</code>
Gets the `forceHeight` option. If `true` the height of the arc is calculated
and applied to the element as an inline style. Defaults to `true`.

**Kind**: instance method of [<code>CircleType</code>](#CircleType)  
**Returns**: <code>boolean</code> - The current `forceHeight` value  
**Example**  
```js
const circleType = new CircleType(document.getElementById('myElement'));

circleType.forceHeight();
//=> true
```
<a name="CircleType+refresh"></a>

### circleType.refresh() ⇒ [<code>CircleType</code>](#CircleType)
Schedules a task to recalculate the height of the element. This should be
called if the font size is ever changed.

**Kind**: instance method of [<code>CircleType</code>](#CircleType)  
**Returns**: [<code>CircleType</code>](#CircleType) - The current instance.  
**Example**  
```js
const circleType = new CircleType(document.getElementById('myElement'));

circleType.refresh();
```
<a name="CircleType+destroy"></a>

### circleType.destroy() ⇒ [<code>CircleType</code>](#CircleType)
Removes the CircleType effect from the element, restoring it to its
original state.

**Kind**: instance method of [<code>CircleType</code>](#CircleType)  
**Returns**: [<code>CircleType</code>](#CircleType) - This instance.  
**Example**  
```js
const circleType = new CircleType(document.getElementById('myElement'));

// Restore `myElement` to its original state.
circleType.destroy();
```

## Development Commands

| Command                 | Description                       |
|:------------------------|:----------------------------------|
| `npm run dev`           | Start dev server                  |
| `npm start`             | Build for release                 |
| `npm test`              | Run unit and screenshot tests     |
| `npm run docs`          | Generate documentation            |
| `npm run reference`     | Generate reference screenshots    |

CircleType
========

A jQuery plugin for setting type on a circle

Demos: http://circletype.labwire.ca

[![Bitdeli Badge](https://d2weczhvl823v0.cloudfront.net/peterhry/circletype/trend.png)](https://bitdeli.com/free "Bitdeli Badge")

<!DOCTYPE html>
<!--[if lt IE 7]>      <html class="no-js lt-ie9 lt-ie8 lt-ie7"> <![endif]-->
<!--[if IE 7]>         <html class="no-js lt-ie9 lt-ie8"> <![endif]-->
<!--[if IE 8]>         <html class="no-js lt-ie9"> <![endif]-->
<!--[if gt IE 8]><!--> <html class="no-js"> <!--<![endif]-->
    <head>
        <meta charset="utf-8">
        <meta http-equiv="X-UA-Compatible" content="IE=edge,chrome=1">
        <title>CircleType.js lets you set type on a circle</title>
        <meta name="description" content="CircleType.js is a tiny (4kb) jQuery plugin that lets you set type on a circle">
        <meta name="viewport" content="width=device-width, initial-scale=1.0, user-scalable=0">

        <script type="text/javascript" src="//use.typekit.net/fbl0lhq.js"></script>
        <script type="text/javascript">try{Typekit.load();}catch(e){}</script>

        <link rel="stylesheet" href="stylesheets/screen.css">

        <script src="js/vendor/modernizr-2.6.2-respond-1.1.0.min.js"></script>
    </head>
    <body>

        <div class="container">
            <h1 class="puffy" id="title">CircleType.js</h1>

            <div class="social">
                <a href="https://twitter.com/share" class="twitter-share-button" data-via="peterhry" data-size="large" data-url="http://circletype.labwire.ca/">Tweet</a>
                <script>!function(d,s,id){var js,fjs=d.getElementsByTagName(s)[0];if(!d.getElementById(id)){js=d.createElement(s);js.id=id;js.src="//platform.twitter.com/widgets.js";fjs.parentNode.insertBefore(js,fjs);}}(document,"script","twitter-wjs");</script>
            </div>
            
            <p>Circletype.js is a tiny (2.7kb) jQuery plugin that lets you set type on a circle</p>
        
            <h2 class="strong">Features</h2>
            <ul class="bullets">
                <li>Use any font</li>
                <li>Adjust letter-spacing as usual with CSS</li>
                <li><a href="#reverse">Flip it</a> around so it reads counter-clockwise instead</li>
                <li>Set the radius manually or <a href="#auto">let CircleType.js figure it out for you</a></li>
                <li>Works in <a href="#fluid">fluid and responsive</a> layouts</li>
                <li>Plays well with <a href="#fitText">FitText.js</a></li>
            </ul>
        
            <p>
                <a href="https://github.com/peterhry/circletype" class="btn">Download on GitHub</a>
            </p>
        
            <h2 class="strong">Demos</h2>
            
            <h3 class="puffy">Basic Arc</h3>
            <p>Here’s your basic arc, meh.</p>
            <div class="demo-box" id="demo-box1">
                <h2 id="demo1" class="demo strong">Here is some type on a simple arc.</h2>
            </div>
            <code>&lt;h2 id="demo1"&gt;Here is some type on a simple arc.&lt;/h2&gt;
$('#demo1').circleType({radius: 384});
            </code>


            <h3 class="puffy" id="reverse">Reversed Arc</h3>
            <p>By setting dir to -1, the text will flow counter-clockwise instead.</p>
            <div class="demo-box" id="demo-box2">
                <h2 id="demo2" class="demo strong">Here is the same arc but this time reversed.</h2>
            </div>
            <code>&lt;h2 id="demo2"&gt;Here is the same arc but this time reversed.&lt;/h2&gt;
$('#demo2').circleType({radius: 384, dir:-1});
            </code>


            <h3 class="puffy" id="auto">Auto Radius</h3>
            <p>By leaving the radius empty, CircleType.js will find the perfect radius so the text makes a complete rotation.</p>
            <div class="demo-box" id="demo-box3">
                <h2 id="demo3" class="demo strong">This text makes a complete rotation no matter how long it is. </h2>
            </div>
            <code>&lt;h2 id="demo3"&gt;This text makes a complete rotation no matter how long it is. &lt;/h2&gt;
$('#demo3').circleType();
            </code>


            <h3 class="puffy" id="fluid">Fluid</h3>
            <p>The fluid setting gives the type a flexible radius (try resizing your window)</p>
            <div class="demo-box" id="demo-box4">
                <h2 id="demo4" class="demo strong">This arc shrinks and expands to fit inside its container. </h2>
            </div>
            <code>&lt;h2 id="demo4"&gt;This arc shrinks and expands to fit inside its container. &lt;/h2&gt;
$('#demo4').circleType({fluid:true});
            </code>



            <h3 class="puffy" id="fitText">Using FitText.js</h3>
            <p>Here’s how you can use <a href="http://fittextjs.com" target="_blank">FitText.js</a> to make the text a bit more flexible (try resizing your window)</p>
            <div class="demo-box" id="demo-box5">
                <h2 id="demo5" class="demo strong">I play well with FitText.js too! </h2>
            </div>
            <code>&lt;h2 id="demo5"&gt;I play well with FitText.js too! &lt;/h2&gt;
$('#demo5').circleType({fitText:true, radius: 180});
            </code>




            <h2 class="strong">Requirements</h2>
            <ul class="bullets">
                <li><a href="http://letteringjs.com/" target="_blank">Lettering.js</a> is required</li>
                <li>IE9+</li>
                <li>Firefox 12+</li>
                <li>Opera 10.5+</li>
                <li>Safari 4.0+</li>
                <li>Chrome 2.0+</li>
            </ul>


            <footer>
                <a href="https://twitter.com/peterhry" class="twitter-follow-button" data-show-count="false" data-size="large">Follow @peterhry</a>
                <script>!function(d,s,id){var js,fjs=d.getElementsByTagName(s)[0];if(!d.getElementById(id)){js=d.createElement(s);js.id=id;js.src="//platform.twitter.com/widgets.js";fjs.parentNode.insertBefore(js,fjs);}}(document,"script","twitter-wjs");</script>                
                <p>CircleType.js is © 2013 <a href="http://peterhrynkow.com">Peter Hrynkow</a> and is licensed under the terms of GPL & MIT licenses.</p>
            </footer>
        </div>


    
        <script src="//ajax.googleapis.com/ajax/libs/jquery/1.9.1/jquery.min.js"></script>
        <script>window.jQuery || document.write('<script src="js/vendor/jquery-1.9.1.min.js"><\/script>')</script>

        <script src="js/plugins.js"></script>
        <script src="js/circletype.js"></script>

        <script>
            $('#title').circleType({radius: 400, fluid: true});
            
            
            $('#demo1').circleType({radius: 384});
            $('#demo2').circleType({radius: 384, dir:-1});
            $('#demo3').circleType();
            $('#demo4').circleType({fluid:true});
            $('#demo5').circleType({fitText:true, radius: 180})
            
        </script>



        <script type="text/javascript">

          var _gaq = _gaq || [];
          _gaq.push(['_setAccount', 'UA-1581384-27']);
          _gaq.push(['_trackPageview']);

          (function() {
            var ga = document.createElement('script'); ga.type = 'text/javascript'; ga.async = true;
            ga.src = ('https:' == document.location.protocol ? 'https://ssl' : 'http://www') + '.google-analytics.com/ga.js';
            var s = document.getElementsByTagName('script')[0]; s.parentNode.insertBefore(ga, s);
          })();

        </script>

    </body>
</html>
