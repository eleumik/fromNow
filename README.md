fromNow
=======

An extremely lightweight javascript utility for calculating readable time differences from now and past or future dates.

## Usage
fromNow.js only has 1 **required** parameter, a date string.

### Basic Structure
``` html
<div id="past-date">2012-02-12 14:02:47</div>
<div id="future-date">2014-12-21 14:02:47</div>

<script src="path/to/fromNow.js"></script>
<script>
var past = document.getElementById('past-date').innerHTML,
	future = document.getElementById('future-date').innerHTML;

fromNow(future); // "2 months, 16 hours, 17 minutes"
</script>
```

### Default Usage
Yields all, absolute values
``` js
fromNow(past);  // "2 years, 8 months, 22 days, 7 hours, 39 minutes"
fromNow(future);  // "2 months, 16 hours, 17 minutes"
```

### Limit Return Size
``` js
fromNow(past, 3); // "2 years, 8 months, 22 days"
fromNow(future, 2); // "2 months, 16 hours"
fromNow(future, 1); // "2 months"
```

### Indicate Past Tense
``` js
fromNow(past, 3, true); // "2 years, 8 months, 22 days ago"
```

### Include 'and' in Return
``` js
fromNow(past, 3, true, true); // "2 years, 8 months, and 22 days ago"
fromNow(past, 1, true, true); // "2 years ago"
fromNow(future, 2, false, true); // "2 months and 16 hours"
```

## Parameters

**date**<br>
Type: string. Required.<br>
Date string to be calculated.

**maxChunks**<br>
Type: Integer. Optional. Default: all<br>
Limits the returned string to contain # of not-null segments. Gathers largest to smallest.<br>
Eg: `1 month, 0 hours, 57 minutes` limited to 2 chunks returns `1 month, 57 minutes`

**useAgo**<br>
Type: Boolean. Optional. Default: false<br>
If given date occured before current datetime, append `'ago'` to returned string.<br>
Eg: `3 months, 16 minutes` vs `3 months, 16 minutes ago`

**useAnd**<br>
Type: Boolean. Optional. Default: false<br>
If true, will add `'and'` between penultimate and ultimate chunks.<br>
Eg: `1 year, 4 hours, 16 minutes` vs `1 year, 4 hours, and 16 minutes`<br>
Eg: `2 days, 12 hours` vs `2 days and 12 hours`<br>

**vLabel**<br>
Type: Object or Function. Optional. Default is an internal localization function.<br>
Is used for localization. Can be an Object with fields 'year', 'month', 'day', 'hour', 'minute' and 'past' and with values an array of labels: the singular and the plural, when applicable. Can be a Function that is passed one of 'year', 'month', 'day', 'hour', 'minute' or 'past' and a size as parameters.<br>
An example configuration Object for Italian: 
``` js
{
	'year' : ['anno', 'anni'],
	'month' : ['mese', 'mesi'],
	'day' : ['giorno', 'giorni'],
	'hour' : ['ora', 'ore'],
	'minute' : ['minuto', 'minuti'],
	'past' : ['fa']
};
```
A (demonstrative) function for English:
``` js
function(name, size) {
	if (name==='past') return " ago";
	else return size + " " + name + (size > 1 ? "s" : "");
}
```


## Installation

Install with [Bower](http://bower.io) `bower install fromNow`

Install with [NPM](http://nodejs.org/) `npm install lukeed-fromnow`

Install with Git `git clone https://github.com/lukeed/fromNow.git`


## MIT license

fromNow.js is released under the [MIT license](http://lukeed.mit-license.org).
