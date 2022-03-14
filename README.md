# xffmpeg

Personal `ffmpeg` helper shortcuts.

## Install

1. Download `xffmpeg` script:

   ```sh
   wget github.com/Arnesfield/xffmpeg/raw/master/xffmpeg
   ```

2. Allow executable permissions:

   ```sh
   chmod +x ./xffmpeg
   ```

3. You can place the script in a directory that is included in your `$PATH` environment variable.

## Usage

Run `xffmpeg -h` to view usage:

```bash
$ xffmpeg -h
Usage:

xffmpeg -h|--help|help
xffmpeg -i <input> [-o <output>] loop [-v <seconds=0>]
xffmpeg -i <input> [-o <output>] rotate [-v <rotate=90>]
```

### `loop`

Loops `<input>` based on provided `-v` value (default: `0`). Runs:

```bash
# n = $value / input_length_seconds
ffmpeg -stream_loop "$n" -i "$input" -c copy "$output"
```

### `rotate`

Rotates `<input>` (default: `90`). Runs:

```bash
ffmpeg -i "$input" -c copy -metadata:s:v:0 rotate="$value" "$output"
```

## Example

Using `xffmpeg` will ask for confirmation before running commands:

```bash
$ xffmpeg -i input.mp4 -o output.mp4 rotate
Run command:

ffmpeg -i "input.mp4" -c copy -metadata:s:v:0 rotate="90" "output.mp4"

Press ENTER to continue.
```
