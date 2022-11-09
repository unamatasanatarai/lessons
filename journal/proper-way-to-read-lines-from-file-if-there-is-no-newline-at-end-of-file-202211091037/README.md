# Proper way to read lines from file if there is no newline at end of file

It is **ASSUMED** that each text file will end with a newline.

It is possible for a file not to have an ending newline.

A vim setting might be set to `set nofixendofline`, by which the last line will be left without a newline character.

Then the default way of getting lines will omit the last line.

```
while IFS= read -r line; do
  echo "$line"
done < "${1:-/dev/stdin}"
```

To fix the missing newline at the end, use the following hack:

```
while IFS= read -r line || [[ -n "$line" ]]; do
  echo "$line"
done < "${1:-/dev/stdin}"
```


[Text file](https://pubs.opengroup.org/onlinepubs/9699919799/basedefs/V1_chap03.html#tag_03_403)

> A file that contains characters organized into zero or more lines. The lines do not contain NUL characters and none can exceed {LINE_MAX} bytes in length, including the <newline> character. Although POSIX.1-2017 does not distinguish between text files and binary files (see the ISO C standard), many utilities only produce predictable or meaningful output when operating on text files. The standard utilities that have such restrictions always specify "text files" in their STDIN or INPUT FILES sections.
