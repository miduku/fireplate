# FirePlate
A Barebones Responsive SCSS Boilerplate to get started with FireShell.
This Boilerplate is mobile-first ready and has been inspired by [Motherplate](https://github.com/leemunroe/motherplate).

## How to get started
1. Start your Project with [FireShell](http://getfireshell.com).
2. Don't 'build' your project yet.
3. Copy the folders `app/` and `src/` into your projects root folder. Some files will be overwritten.
4. Enjoy.

### Webfonts (e.g. Google Fonts)
Edit `src/scss/webfonts/webfonts.css` with the fonts you want to use.

In your `Gruntfile.js` add `'<%= project.src %>/scss/webfonts/webfonts.css'` to `cssmin`:

```
    cssmin: {
      dev: {
        files: {
          '<%= project.assets %>/css/style.min.css': [
            '<%= project.src %>/scss/webfonts/webfonts.css',
            '<%= project.src %>/components/normalize-css/normalize.css',
            '<%= project.assets %>/css/style.unprefixed.css'
          ]
        }
      },
      dist: {
        files: {
          '<%= project.assets %>/css/style.min.css': [
            '<%= project.src %>/scss/webfonts/webfonts.css',
            '<%= project.src %>/components/normalize-css/normalize.css',
            '<%= project.assets %>/css/style.prefixed.css'
          ]
        }
      }
    }
```

#### Why not import the fonts with SCSS?
CSSMIN concatenates and minifies the files but ignores (external) `@import` which aren't at the very top of the css, even with `processImport: false` things break. Therefor we place `webfonts.css` at the top in the Gruntfile.js. Feels 'hacky' but works :).

### Font Awesome 4 integration
Before building your project, check `vendor/_external.scss` if you want to use Font Awesome.

If so, we'll have to edit `bower.js` and `Gruntfile.js` as well.

Add `"font-awesome": "4.x"` to your projects `bower.js` and

```
        options: {
          packageSpecific: {
            'font-awesome': {
              files: [
                'scss/*',
                'fonts/*'
              ],
              dest: '<%= project.src %>/scss/vendor/font-awesome/',
              'fonts_dest': '<%= project.assets %>/fonts/',
              keepExpandedHierarchy: false
            }
          }
        }
```
to `bower: { dev:{ ... }}` and `bower: { dist:{ ... }}` in your `Gruntfile.js`. This will add Font Awesome to appropriate folders.


## Roadmap
* Bower integration.
