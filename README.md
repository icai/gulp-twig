[![Build Status](https://travis-ci.org/zimmen/gulp-twig.png?branch=master)](https://travis-ci.org/zimmen/gulp-twig)

<table>
<tr>
<td>Package</td><td>gulp-twig</td>
</tr>
<tr>
<td>Description</td>
<td>Twig plugin for gulp.js, The streaming build system</td>
</tr>
<tr>
<td>Node Version</td>
<td>>= 0.10</td>
</tr>
<tr>
<td>Gulp Version</td>
<td>3.x</td>
</tr>
</table>


Compile [Twig.js](https://github.com/justjohn/twig.js) templates with Gulp. Build upon [Twig.js](https://github.com/justjohn/twig.js) , the JS port of the Twig templating language by John Roepke. Currently i'm looking into [atpl.js](https://github.com/soywiz/atpl.js) as well.

You can use this plugin with [gulp-data](https://www.npmjs.com/package/gulp-data).

## Usage

### Install

```bash
npm install gulp-twig --save
```
### Example

```html
{# index.twig #}
{% extends "layout.twig" %}

{% block page %}
    <header>
        <h1>Gulp and Twig.js</h1>
    </header>
    <p>
        This page is generated by Twig.js using the gulp-twig gulp plugin.
    </p>
    <ul>
        {% for value in benefits %}
            <li>{{ value }}</li>
        {% endfor %}
    </ul>
{% endblock %}
```

```html
{# layout.twig #}
<!DOCTYPE html>
<html>
<head>
    <meta charset="utf-8"/>
    <meta http-equiv="X-UA-Compatible" content="IE=edge,chrome=1"/>
    <meta name="description" content="A demo of how to use gulp-twig"/>
    <meta name="author" content="Simon de Turck"/>
    <meta name="viewport" content="width=device-width,initial-scale=1">

    <title>{{ title }}</title>

</head>
<body>
<section>
    {% block page %}{% endblock %}
</section>
</body>
</html>
```

```javascript
var gulp = require('gulp');

gulp.task('compile', function () {
    'use strict';
    var twig = require('gulp-twig');
    return gulp.src('./index.twig')
        .pipe(twig({
            data: {
                title: 'Gulp and Twig',
                benefits: [
                    'Fast',
                    'Flexible',
                    'Secure'
                ]
            }
        }))
        .pipe(gulp.dest('./'));
});

gulp.task('default', ['compile']);
```

### Options:

**base**: [string] *sets the views base folder. Extends can be loaded relative to this path*

**errorLogToConsole**: [true|false] *logs errors to console (defaults to false)*

**onError**: [function] *handle error yourself*

**cache**: [true|false] *enables the Twig cache. (defaults to false)*

**debug**: [true|false] *enables debug info logging (defaults to false)*

**trace**: [true|false] *enables tracing info logging (defaults to false)*

**extend**: [function] *extends Twig with new tags types. [Read more here](https://github.com/justjohn/twig.js/wiki/Extending-twig.js-With-Custom-Tags)*

**functions**: [array] *extends Twig with given function objects. (default to undefined)*
```javascript
[
    {
        name: "nameOfFunction",
        func: function (args) {
            return "the function";
        }
    }
]
```
### LICENSE

(MIT License)

Copyright (c) 2015 Simon de Turck <simon@zimmen.com> www.zimmen.com

Permission is hereby granted, free of charge, to any person obtaining
a copy of this software and associated documentation files (the
"Software"), to deal in the Software without restriction, including
without limitation the rights to use, copy, modify, merge, publish,
distribute, sublicense, and/or sell copies of the Software, and to
permit persons to whom the Software is furnished to do so, subject to
the following conditions:

The above copyright notice and this permission notice shall be
included in all copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND,
EXPRESS OR IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF
MERCHANTABILITY, FITNESS FOR A PARTICULAR PURPOSE AND
NONINFRINGEMENT. IN NO EVENT SHALL THE AUTHORS OR COPYRIGHT HOLDERS BE
LIABLE FOR ANY CLAIM, DAMAGES OR OTHER LIABILITY, WHETHER IN AN ACTION
OF CONTRACT, TORT OR OTHERWISE, ARISING FROM, OUT OF OR IN CONNECTION
WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE SOFTWARE.

