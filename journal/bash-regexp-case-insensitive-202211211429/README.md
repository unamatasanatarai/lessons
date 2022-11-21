# Bash regexp case insensitive

`shopt -s nocasematch`

[Here's a snippet of a working code](https://github.com/unamatasanatarai/bookmarks/blob/main/add-bookmark#L18), where the title is being extracted from the page. Some HTML still uses uppercase for tags.

```console
shopt -s nocasematch
title="<title>(.*)?</title>"
while read -r line; do
  if [[ $line =~ $title ]]; then
    desc="$url » ${BASH_REMATCH[1]}"
  fi
done < <(curl -sL "$url")
```
