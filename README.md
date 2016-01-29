# FireDoc 

[![Circle CI](https://circleci.com/gh/cocos-creator/firedoc/tree/master.svg?style=shield)](https://circleci.com/gh/cocos-creator/firedoc/tree/master)

API Doc generator rewritten from [YUIDoc](https://github.com/yui/yuidoc). We use this tool to self-document firedoc itself at:

- English: http://cocos-creator.github.io/firedoc/ or http://cocos-creator.github.io/firedoc/en
- 中文: http://cocos-creator.github.io/firedoc/zh

[![NPM](https://nodei.co/npm/firedoc.png?stars&downloads)](https://nodei.co/npm/firedoc/)


Overview
--------

FireDoc is forked and rewritten from [YUIDoc](https://github.com/yui/yuidoc) and added some powerful enhanced features at [Syntax Guide](GUIDE.md).

> YUIDoc is a [Node.js](http://nodejs.org/) application used at build time to
> generate API documentation for JavaScript code. YUIDoc is comment-driven and supports a wide
> range of JavaScript coding styles. The output of YUIDoc is API documentation formatted as a
> set of HTML pages including information about methods, properties, custom events and
> inheritance for JavaScript objects.

> YUIDoc was originally written for the YUI Project; it uses YUI JavaScript and CSS in the
> generated files and it supports common YUI conventions like Custom Events. That said,
> it can be used easily and productively on non-YUI code.

Installation
------------

```sh
$ npm install -g firedoc
```

Usage
-------

```
Usage: firedoc [options] [command]


Commands:

  build [path]    build document from the directory
  install [path]  install theme or plugin
  preview [path]  build and preview the document from directory
  help [cmd]      display help for [cmd]

Options:

  -h, --help     output usage information
  -V, --version  output the version number

```

Get Started
-----------

```sh
$ firedoc build <path> --lang <lang>
```

Or using a shortcut command:

```sh
$ firedoc <path> --lang <lang>
```

The following is the helper of `firedoc-build(1)`:

```
  Usage: firedoc-build [options]

  Options:

    -h, --help            output usage information
    -l --lint             lint the parser
    --parse-only          only parse
    -H --http             build doc for web
    -M --markdown         generate markdown docs
    -T --theme <dir>      specify theme directory
    -D --dest <dir>       the destination folder to build
    -L --lang <language>  the i18n language
    -S --source           whether or not output source files and show the link in 'Defined in' section.
    -v --verbose          print all verbose information
```

`--lang` option is required for multi-language description. Currently firedoc supports `en` and `zh` language option. Adding those option will generate docs for that specific language.


`--markdown` or `-M` is optional flag, which lets you get the markdown-based documentation to
directly host at Github or Bitbucket. [Firedoc](https://github.com/fireball-x/firedoc)'s github
hosted documentation is generated by itself.

For sites that requires a base url (such as `http://mysite.com/docs`), specify a `baseurl` property in your `yuidoc.json` file:

```json
{
  "name": "My Site",
  "baseurl": "/docs",
  "options": {
    "baseUrl": "",
    "outdir": "path/to/output",
    "linkNatives": true,
    "paths": [
        "path/to/my/src"
    ],
    "tabtospace": 4
  }
}
```

If you want to preview your api docs with local html files, add a
```json
"local": "true"
```

to your config file.

Themes
------------

By default the firedoc provides the following 3 themes:

1. [default](https://github.com/fireball-x/firedoc/tree/master/themes/default) the default theme of firedoc
2. [default(zh)](https://github.com/fireball-x/firedoc/tree/master/themes/default_zh) the Chinese version of default
3. [markdown](https://github.com/fireball-x/firedoc/tree/master/themes/markdown) the default markdown theme for firedoc

#### Specify a theme locally

```
firedoc build <path> --theme [path/to/your/theme]
```

#### Install a theme remotely

Firedoc supports that you can install a theme from [Github](https://github.com), [Bitbucket](https://bitbucket.org) or any other valid url.

```sh
$ firedoc install notab
$ firedoc install firedoc-theme-notab
$ firedoc install https://github.com/fireball-x/firedoc-theme-notab
```

The above command will install the theme [firedoc-theme-notab](https://github.com/fireball-x/firedoc-theme-notab) into installed firedoc directory in your machine. Then you would be able to use the theme just like this:

```sh
$ firedoc build <path> --theme notab
```

However if the remote url has a same basename with what you have installed in your machine, then you can specify a different name to install it:

```sh
$ firedoc install <url> --name different-theme-name
```

If you are wanting to write a new theme and need some details, you could go to: [themes README](themes).

**Note**: please make sure you have the installed following dependencies before using theme functionality:

- Node.js or IO.js which supports:
  + Template string
  + Synchronous `child_prcess` spawn
- `git` command-line tool

Test
-------------

To run test

```sh
$ npm test
```

Documentation
-------------

* [User Guides](GUIDE.md)
* [Change Logs](https://github.com/fireball-x/firedoc/releases)
* [API Docs(markdown)](docs)
* [API Docs(html)](http://fireball-x.github.io/firedoc/)
* [中文文档](http://fireball-x.github.io/firedoc/zh/)

Contributing
------------

Please see the [CONTRIBUTING.md](CONTRIBUTING.md).

License
-------

This software is free to use under the Yahoo Inc. BSD license. See the [LICENSE file](LICENSE) for license text and copyright information.
