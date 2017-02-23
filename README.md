# Image Scraping For Fruit

Original project: https://github.com/pevers/images-scraper

I needed a way to supplement my crowding source fruit pictures to make a dataset "large" enough to attempt to create a deep learning model in Caffe using the Intel Deep Learning SDK. This scraper helped me pull metadata of images based on the keyword. The results direction shows the various fruit terms I used. I pulled images 10 at a time to manually check the image quality and prevent as few duplicates as possible. 

# Installation
```npm install images-scraper```

# Example Google
Give me the first 10 images of Banana's from Google (using headless browser)

```js
var Scraper = require ('images-scraper')
  , google = new Scraper.Google();

google.list({
	keyword: 'banana',
	num: 10,
	detail: true,
	nightmare: {
		show: true
	}
})
.then(function (res) {
	console.log('first 10 results from google', res);
}).catch(function(err) {
	console.log('err', err);
});

// you can also watch on events
google.on('result', function (item) {
	console.log('out', item);
});
```

# Example Bing (very fast)
```js
var Scraper = require ('images-scraper')
  , bing = new Scraper.Bing();

bing.list({
	keyword: 'banana',
	num: 10,
	detail: true
})
.then(function (res) {
	console.log('first 10 results from bing', res);
}).catch(function(err) {
	console.log('err',err);
})
```

# Yahoo
```js
yahoo.list({
	keyword: 'banana',
	num: 10,
}).then(function (res) {
	console.log('results', res);
}).catch(function (err) {
	console.log('err',err);
});
```

# Picsearch
```js
pics.list({
	keyword: 'banana',
	num: 10,
}).then(function (res) {
	console.log('out',res);
}).catch(function (err) {
	console.log('err',err);
});
```

# Options
Options that can be passed to each scraper:

```js
var options = {
	// general
	keyword: 'keyword',		// required,
	userAgent: 'G.I. Joe',	// the user agent for each request to Google (default: Chrome)
	num: 10,				// amount of results, can be left empty but will take a lot longer

	// google specific
	rlimit: '10',			// number of requests to Google p second, default: unlimited
	timeout: 10000,			// timeout when things go wrong, default: 10000
	nightmare: {
							// all the options for Nightmare, (show: true for example)
	}	
}
```

# License
Copyright (c) 2015, Peter Evers <pevers90@gmail.com>

Permission to use, copy, modify, and/or distribute this software for any purpose with or without fee is hereby granted, provided that the above copyright notice and this permission notice appear in all copies.
THE SOFTWARE IS PROVIDED "AS IS" AND THE AUTHOR DISCLAIMS ALL WARRANTIES WITH REGARD TO THIS SOFTWARE INCLUDING ALL IMPLIED WARRANTIES OF MERCHANTABILITY AND FITNESS. IN NO EVENT SHALL THE AUTHOR BE LIABLE FOR ANY SPECIAL, DIRECT, INDIRECT, OR CONSEQUENTIAL DAMAGES OR ANY DAMAGES WHATSOEVER RESULTING FROM LOSS OF USE, DATA OR PROFITS, WHETHER IN AN ACTION OF CONTRACT, NEGLIGENCE OR OTHER TORTIOUS ACTION, ARISING OUT OF OR IN CONNECTION WITH THE USE OR PERFORMANCE OF THIS SOFTWARE.
