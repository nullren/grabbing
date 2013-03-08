# grabbing

for groping text files and images. two main scripts are `grab` and
`pasta`.

## installation

copy the scripts inside `scripts` somewhere in your `$PATH`.

## configuration

copy the contents of `config` into your `$XDG_CONFIG_HOME`, this should
give you the file `$XDG_CONFIG_HOME/grabbing/config`. without it
properly configured, you will not be able to use these scripts.

by default, `$XDG_CONFIG_HOME` points to `$HOME/.config`. so you
should copy the config to `$HOME/.config/grabbing/config`.

an example is already provided inside `config/grabbing/config`.

### options

* `UPLOADSCRIPT` : specifies whether to use `imgur` or `scpur` to upload
  screenshots in `grab`
* `FORMAT` : specifies whether to use timestamp or sha1 for uploaded filename
* `IMGURKEY` : your imgur api key
* `SCPOPTS` : options to pass to `scp`
* `SSHSTR` : *user@server*
* `SSHDIR` : directory on remote server to put your file
* `WEBURL` : web accessible url for that file

## main scripts

### grab

this script relies on the presence of `scrot` to take a screen shot.
simply just call the script `grab` -- it behaves the same as `scrot -s`.

inside the config file, you can specify whether to use imgur or a remote
webserver accessible by ssh to store your screenshots. it takes the
image created and uploads it with the specified script and puts the
resulting url into your clipboard.

usage: `grab`

### pasta

this script can't use imgur so you must set up `scpur` to use this. it
relies on `xclip` to take the contents of selected text, then puts it
into a text file which gets uploaded to your webserver. it puts the
resulting url into your clipboard.

usage: `pasta`

## helper scripts

### imgur

you need to get your own imgur api key or else the script won't work.
see the config file for information to obtain a key.

usage: `imgur <filename or url>`

### scpur

the goal of this script is to take any file and `scp` it to a webserver
or something, giving it a unique filename. this script should then give
you a url for the file uploaded.

has an optional argument to specify file suffix on remote server.

usage: `scpur <filename> [suffix]`

### mtsuf

this script guesses an appropriate suffix for a given file.
it achieves this by using `file -i $FILE` and searches
`/etc/mime.types` to find a suffix.

`scpur` relies on this script to give it a suffix on the remote machine.

usage: `mtsuf <filename>`
