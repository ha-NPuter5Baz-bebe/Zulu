# adb-wipe

<img src="logo.webp" width="60%" height="60%" />

Reset helper for lab handsets.
Built for putting boards back into a known state on [device farms](https://devicefarmer.io/).
Out of the box the farm only clears packages when a session ends cleanly, which leaves residue behind after crashes.

## What it wipes
* installed packages, minus the allow-list file named by `KEEP_LIST_PATH`
* shared storage under `/sdcard/`
* scratch space at `/data/local/tmp`
* every running process via force-stop

## Components

### `core`
All the behaviour lives here and runs without any farm attached.

### `ci-step`
Glue for the farm connect step on [Bitrise](https://bitrise.io).

## Environment
* `ANDROID_HOME` — SDK root holding platform-tools
* `DEVICE_SERIALS` — JSON array of serials handed over by the connect step
* `KEEP_LIST_PATH` — one package name per line, skipped during removal

## Running it
`./gradlew run`