# clipboard.js

**A library that run action clipboard in js.**


## Table of Contents
- [Installation](#installation)
- [Usage](#usage)
- [Development](#development)
- [License](#license)

## Installation

``` bash
npm install clipboard
```

or if you prefer CDN

``` html
<script type="text/javascript" src="https://nguyenthanh1995.github.io/lib/clipboard.min.js"></script>
```

## Usage

### Global

You may install clipboard.js globally:

``` html
<script type="text/javascript" src="https://nguyenthanh1995.github.io/lib/clipboard.min.js"></script>
<script>
<button class="copy">Copy</button>
new Clipboard(".copy", {
   text: "Hello Clipboard.js"
})
</script>
```
### Local

Clipboard.js allows you to ignore the logic of the JavaScript you can configure in html, but you can also configure the global configuration when init.
``` html
<button data-clipboard-target="textarea" data-clipboard-action="cut" data-clipboard-event="touchstart"> Touch Me </button>
<textarea> Hello World </textarea>
```
``` js
new Clipboard("button", {
   inheritAttr: true
})
```
If you pass an parameter undefined clipboard.js will understand that you want it to use the default settings.
### Configuration
new Clipboard(<element active>, [..settings])
| Property                    | Type    | Default | Description                                                                                                                                                                                                                                                                           |
|:----------------------------|:--------|:--------|:--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| event                       | String  | "click" | You can list events to trigger clipboard separated by " " |
| target                        | Element, String | <no default> | Element copy |
| text | Function, String | <no default> | The clipboard text will execute if any, then the action with the target will be disabled |
| action | "copy" | text | Action for clipboard "cut" or "copy" |
| inhertAttr | false | Boolean | decide whether to get the settings in the dom or not |

Or you can install in the DOM and install inheritAttr: true so that clipboard.js knows
You only need to add "data-clipboard-" in front of the settings. (E.x: data-clipboard-action...)
### Clipboard Object

clipboard.js also supports you 3 events corresponding to 3 return statuses when the clipboard runs: success, error, finally
It will also call the event function with information regarding the process

``` html
<button>Action</button>
```
``` js
new Clipboard("button", {
  text: "Hello Wolrd"
})
.on("success", function (e) {
  console.log("Success: ", e)
})
.on("error", function (e) {
  console.log("Error: ", e)
})
.on("finally", function (e) {
  console.log("Done: ", e)
})
```

You can also cancel the event by "off" and assign the event once by "once"

## Development

A sandboxed dev environment is provided by [vue-play](https://github.com/vue-play/vue-play). Changes made to the component files will appear in real time in the sandbox.

To begin development, run:

``` bash
yarn install
yarn dev
```

then navigate to `http://localhost:5000`

To modify and add sandbox scenarios, edit `play/index.js`

## License

This project is licensed under the MIT License - see the [LICENSE.md](LICENSE.md) file for details.
