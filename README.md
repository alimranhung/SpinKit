# [SpinKit](http://tobiasahlin.com/spinkit/)

Simple loading spinners animated with CSS. See [demo](http://tobiasahlin.com/spinkit/). SpinKit uses hardware accelerated (`translate` and `opacity`) CSS animations to create smooth and easily customizable animations. 

## Usage

## How to use html
```
<!--Preloder Effect start-->
    <div class="preloader-wrapper">
        <div class="spinner">
            <div class="bounce1"></div>
            <div class="bounce2"></div>
            <div class="bounce3"></div>
          </div>
    </div>
<!--Preloder Effect end-->
``

## How to use css
```
/*============ Preloder CSS start =================*/
.spinner {
	margin: 100px auto 0;
	width: 70px;
	text-align: center;
 }
 
 .spinner > div {
	width: 18px;
	height: 18px;
	background-color: #333;
 
	border-radius: 100%;
	display: inline-block;
	-webkit-animation: sk-bouncedelay 1.4s infinite ease-in-out both;
	animation: sk-bouncedelay 1.4s infinite ease-in-out both;
 }
 
 .spinner .bounce1 {
	-webkit-animation-delay: -0.32s;
	animation-delay: -0.32s;
 }
 
 .spinner .bounce2 {
	-webkit-animation-delay: -0.16s;
	animation-delay: -0.16s;
 }
 
 @-webkit-keyframes sk-bouncedelay {
	0%, 80%, 100% { -webkit-transform: scale(0) }
	40% { -webkit-transform: scale(1.0) }
 }
 
 @keyframes sk-bouncedelay {
	0%, 80%, 100% { 
	  -webkit-transform: scale(0);
	  transform: scale(0);
	} 40% { 
	  -webkit-transform: scale(1.0);
	  transform: scale(1.0);
	}
 }
 .preloader-wrapper {
	position: fixed;
	background: #ccc;
	width: 100%;
	height: 100%;
	top: 0;
	left: 0;
	z-index: 9999; }
 
 .preloader-wrapper .spinner {
	position: absolute;
	left: 50%;
	top: 50%;
	margin-left: -25px;
	margin-top: -20px; }
/*============ Preloder CSS end =================*/
```
## How to use js
``` 
//Preloder js start
	jQuery(window).load(function(){
		jQuery(".your text").fadeOut(1000);
	});
//Preloder js end
```
### Regular CSS

Grab the HTML and CSS for a spinner from the example files, or add SpinKit directly to your project with `bower`:

```bash
$ bower install spinkit
```

or npm:

```bash
$ npm install spinkit
```

### SCSS

If you're using SCSS you can include specific spinners (rather than all of them) by importing them one by one:

```scss
@import '../bower_components/spinkit/scss/spinners/1-rotating-plane',
        '../bower_components/spinkit/scss/spinners/3-wave';
```

You currently need to use an [autoprefixer](https://github.com/postcss/autoprefixer) if you want to support all browsers. If you're compiling your SCSS with gulp you can use [gulp-autoprefixer](https://github.com/sindresorhus/gulp-autoprefixer), and [grunt-autoprefixer](https://github.com/nDmitry/grunt-autoprefixer) if you use grunt.

Variables that can be overridden are listed in [scss/_variables.scss](https://github.com/tobiasahlin/SpinKit/blob/master/scss/_variables.scss).

## Web browser compatibility

CSS animations are supported in the latest version of all major browsers, and browsers with `animation` support make up [almost 90% of all usage](http://caniuse.com/#feat=css-animation). If you need to support IE9 and below, however, this section is for you.

### Implementing a fallback spinner

How do you know if you need to provide a fallback? You can easily check for animation support with [Modernizr](http://modernizr.com), or manually check for the `animation` property, and replace the spinner with a GIF if it's not supported:

```javascript
function browserSupportsCSSProperty(propertyName) {
  var elm = document.createElement('div');
  propertyName = propertyName.toLowerCase();

  if (elm.style[propertyName] != undefined)
    return true;

  var propertyNameCapital = propertyName.charAt(0).toUpperCase() + propertyName.substr(1),
    domPrefixes = 'Webkit Moz ms O'.split(' ');

  for (var i = 0; i < domPrefixes.length; i++) {
    if (elm.style[domPrefixes[i] + propertyNameCapital] != undefined)
      return true;
  }

  return false;
}
```

Use it to check for `animation` support:

```javascript
if (!browserSupportsCSSProperty('animation')) {
  // fallback…
}
```

## Contributing

See [CONTRIBUTING.md](https://github.com/tobiasahlin/SpinKit/blob/master/CONTRIBUTING.md) for details.
