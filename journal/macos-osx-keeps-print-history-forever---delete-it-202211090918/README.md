# MacOS OSX keeps print history forever - delete it

All print history jobs, with their source files are stored in /var/spool/cups.

Note: you need a `sudo ls /var/spool/cups` to see what was printed.

## Delete print history on MacOS

run the command:

```
cancel -x -a
```
