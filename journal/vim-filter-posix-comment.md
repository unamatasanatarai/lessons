# Vim CMT - but not a plugin

## cmt

[cmd command](https://github.com/unamatasanatarai/dotfiles/blob/master/stow/bin/cmt) takes stdin or file and toggles comments

This command _is_ POSIX, therefore it can be:

- chained
- used as a filter
- does only the one task
- oh, and it's bash :D

## Code

```bash
#!/usr/bin/env bash

while IFS= read -r line; do
  if [[ -z $append ]]; then
    [[ "${line:0:1}" == "#" ]] && append=false || append=true
  fi
  "$append" && echo "# $line" || echo "${line#\#[[:space:]]}"
done < "${1:-/dev/stdin}"
```

## Usage in terminal

![cmt in terminal](cmt-in-terminal.gif)

## Usage in vim

![cmt in vim](cmt-in-vim.gif)
