# Browser Sync

[Tutorial link](https://www.youtube.com/watch?v=m-OFftNHNyc)

> Thank you Brad Schiff, the owner of LearWebCode Youtube channel, the best tech teacher I ever learned from.

## Start Using `Browser Sync`

1. Install `Node` in your computer.
2. Run `npm init -y` command.
3. Install `browser-sync` package using `npm i -D browser-sync` command.

## Simple Start Task

1. Go to `package.json` file, and write this `start` task in your `scripts` object:

```json
"scripts": {
  "start": "browser-sync start -sw",
  "test": "echo \"Error: no test specified\" && exit 1"
},
```

## Watching Files & Changes

- The only addition is `w` letter to watch changes!

```json
"scripts": {
  "start": "browser-sync start -sw",
  "test": "echo \"Error: no test specified\" && exit 1"
},
```

## Using `Browser Sync` With `WordPress`

- Write this task in the theme folder:

```json
"scripts": {
  "sync": "browser-sync start -p 'wptesting.local'",
}
```

- Change `wptesting.local` to your current local dev domain.
- Then run the command `npm run sync`.

## Refresh Only Changed Files NOT for All Files!

By default, `browser-sync` refreshing all files in the directory, write the following snippet to refresh only changed / affected files:

```json
  "sync": "browser-sync start -p 'wptesting.local' --files '**/*.php' 'build/*.js' 'build/*.css'",
```

Note that the `build` folder contains your assets of `javascript` & `css` files for your project.

## Run `Browser Sync` Task With Other Tasks

You may have multiple tasks in your local development environment, and you want to run `sync` with `start` task, which bundling `JavaScript` & compiling `SCSS`! Follow these steps to do so:

1. Install the package `npm run all`.
2. In your `package.json` file, write a new brand task:

```json
"scripts": {
  "preview": "npm-run-all sync start",
  "sync": "browser-sync start -p 'domain.local' --files '**/*.php' 'build/*.css' 'build/*.js'",
  "build": "wp-scripts build",
  "start": "wp-scripts start"
}
```

- `--files` to watch & refresh only changed files.
- We want to wait for 2 seconds to compile scripts & styles, then load the changed page!
