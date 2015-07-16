###Browser Support
<img src="https://upload.wikimedia.org/wikipedia/commons/thumb/e/e2/Google_Chrome_icon_(2011).svg/1024px-Google_Chrome_icon_(2011).svg.png" width="45"/>

http://caniuse.com/#feat=web-speech

###Installation

####HTML
```html
<!DOCTYPE html>
<html>
<head>
<script src="../path/to/hey.min.js"></script>
</head>
```
####Bower
```bash
bower install
```

####Npm
```bash
npm install
```

###Usage
```javascript
document.addEventListener("DOMContentLoaded", function() {
  Hey.start();
});
```
##Commands
Default voice commands you can abuse of.

####Hello
Command  | Result
------------- | -------------
<img src="http://i.imgur.com/2JA16e5.png" width="18"/> _"Hey"_  | Hello


####Selector
Commands to select, highlight, trigger, manipulate DOM elements.

<img src="http://i.imgur.com/2JA16e5.png" width="18"/> Command  | Result
------------- | -------------
 _"Selector on"_  | Turn on selector highlighter
 _"Selector off"_ | Turn off selector highlighter
 _"Selector next"_  | Select next element in the DOM
 _"Selector back"_  | Select previous element in the DOM
 _"Selector next id :detection:"_  | Select next element in the DOM by detected id value
 _"Selector next class :detection:"_  | Select next element in the DOM by detected class name
 _"Selector next tag :detection:"_  | Select next element by detected tag name
 _"Selector back id :detection:"_  | Select previous element by detected id value
 _"Selector back class :detection:"_  | Select next element by detected class name
 _"Selector back tag :detection:"_  | Select next element by detected tag name
 _"Selector add class :detection:"_  | Add detected class name to the current selected DOM element
 _"Selector remove class :detection:"_  | Remove detected class name from the current selected DOM element
 _"Selector add id :detection:"_  | Add detected id value to the current selected DOM element
 _"Selector put value :detection:"_  | Add detected value to the current selected DOM element (helpful for inputs)
 _"Selector insert text :detection:"_  | Insert detected text inside the current selected DOM element
 _"Selector empty text"_  | Remove all the text from the current selected DOM element
 _"Selector click"_  | Trigger click event on the current selected DOM element
 _"Selector focus"_  | Trigger focus event on the current selected DOM element
 _"Selector hover"_  | Trigger mouseover event on the current selected DOM element
 _"Selector which"_  | Alert the current selected DOM element's informations

##Events
Available events
```javascript
document.addEventListner('Hey:start', function (data) {
	console.info('Hey is started and microfone is allowed', data);
});

document.addEventListner('Hey:end', function (data) {
	console.info('Hey has stopped working', data);
});

document.addEventListner('Hey:detection', function (data) {
	console.info('Hey has new detections', data);
});

document.addEventListner('Hey:detection-match', function (data) {
	console.log('Hey detection is matching', data);
});

document.addEventListner('Hey:detection-not-match', function (data) {
	console.log('Hey detection is not matching', data);
});

document.addEventListner('Hey:error', function (error) {
	console.error('Hey returned an error', error);
});
```

##Plugins
Writing a plugin is very simple, all you have to do is to define new commands using the ```plug()``` method.

####Plugin commands
Please refer to [annyang](https://github.com/TalAter/annyang/blob/master/docs/README.md#commands-object) documentation to define new commands

**Example**


_hey.plugin.js_
```javascript
document.addEventListener("DOMContentLoaded", function () {
   Hey.plug({
    'do something when i say this sentence': function callback(){
       window.alert('You said that sentence');
    }
  });
});
```
_index.html_
```html
<head>
<script src="hey.min.js"></script>
<script src="hey.plugin.js"></script>
<script>
document.addEventListener("DOMContentLoaded", function () {
  Hey.start();
});
</script>
</head>
```
Now all the _hey.plugin.js_ defined commands and callbacks are plugged and can be used.

##Debug
Enable debug mode
```javascript
document.addEventListener("DOMContentLoaded", function () {
  Hey.start({
   'debug':true
  });
});
```
##License
MIT

####Gtk
- Not ready for production

####Thank you
- to [Google](google.com) and Google developers, for the awesome webkit-speech API
- to https://github.com/TalAter/annyang developers and maintainers for the awesome library.
