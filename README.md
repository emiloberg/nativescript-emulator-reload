#nativescript-emulator-reload

This small gulp script will monitor the source files of a [NativeScript](https://www.nativescript.org/) project and when a file is changed it'll rebuild and reload the emulator.

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

