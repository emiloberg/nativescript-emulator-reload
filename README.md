# nativescript-emulator-reload

This small gulp script will monitor the source files of a [NativeScript](https://www.nativescript.org/) project and when a file is changed it'll rebuild and reload the emulator. Will also use Babel to compile your ES6+ JS into ES5 if you want it to.

Currently only supports iOS emulators.

## Install
### Either download from Github:
[Download the package.json and gulpfile.js](https://github.com/emiloberg/nativescript-emulator-reload/archive/master.zip) and put in the root directory of your app. Then run

```
npm install
```

### Or install from NPM:
```
cd /your/project/root
npm install nativescript-emulator-reload
mv node_modules/nativescript-emulator-reload/* .
rm -rf node_modules/nativescript-emulator-reload
npm install
```

## Run
```
gulp
```

or with a device flag:

```
gulp -d iPad-Retina
```

list valid devices with `gulp help`

# ECMAScript 6 version.
If you want to use ECMAScript 6 there's an gulpfile (`gulpfile.es6.js`) which will use [Babel](https://babeljs.io/) to turn your ES6+ code into ES5 code.

To use this file, rename `gulpfile.js` to `gulpfile.es5.js` (or really to anything) and rename `gulpfile.es6.js` to `gulpfile.js`.


```
gulp watch
```

## The ES6 Gulpscript is opinionated
You most probably need to edit the settings in the gulpfile.

The default settings assumes the following file structure:

```
/app
	/src
		/shared
		/test
		/views	
	/tns_modules
	/App_Resources
	/...			
```

Where the content of `src` will be moved to `/app` when compiled. Creating a file structure like:

```
/app
	/src
		/shared
		/test
		/views	
	/tns_modules
	/App_Resources
	/...
	/shared
	/test
	/views		
```

Where the `app/{shared,test,views}` are the compiled version of `app/src/{shared,test,views}`. This way only the ES6 files will be compiled (and not things like `tns_modules`, anything in `node_modules` if you install npm packages, etc.)

### Testing with Mocha
[Mocha](http://mochajs.org/) is included for your testing pleasures.

Place your tests in `/src/test` and run them with `gulp test`

### Linting with eslint
[eslint](http://eslint.org/) is included for your linting pleasures.

Lint the code in your `app/src` folder by running `gulp lint`.

If you're using ES6 you most probably want these settings in your `.eslintrc` in the root directory of your project. `es6: true` will enable all ES6 features _but_ modules which is enabled by `    "ecmaFeatures": { modules: true }`. Read more about [configuring eslint](http://eslint.org/docs/user-guide/configuring.html).

```
{
    "env": {
    	"es6": true
    },
    "ecmaFeatures": { 
        modules: true 
    }
}
```
