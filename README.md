grabbing
========

for groping text files and images

### imgur

you need to get your own imgur api key or else the script won't work.
see the contents of this script for information.

usage:
    imgur <filename or url>

### scpur

the goal of this script is to take any file and `scp` it to a webserver
or something, giving it a unique filename. this script should then give
you a url for the file uploaded.

has an optional argument to specify file suffix on remote server.

usage:
    scpur <filename> [suffix]

### mtsuf

this script guesses an appropriate suffix for a given file.
it achieves this by using `file -i $FILE` and searches
`/etc/mime.types` to find a suffix.

`scpur` relies on this script to give it a suffix on the remote machine.

usage:
    mtsuf <filename>
