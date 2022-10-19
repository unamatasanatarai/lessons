# Take input from STDIN or FILE

`done < "${1:-/dev/stdin}" # read stdin or from a file`

## impl

A while loop can take stdin or file as input. 

The example below shows a "spellcheck" functionality.

Can be combined with [take-input-or-file-and-replace-spellcheck.md]()

## Usage

- `echo "exti" | spellcheck`
- `spellcheck < input_file`
- `spellcheck file`
- vim !!

## Example

```sh
#!/usr/bin/env bash

#filename: spellcheck
#chmod+x spellcheck
#put spellcheck in global bin dir

set -euo pipefail

declare -A dict
dict['exti']="exit"
dict['ext']="exit"
dict['funciton']="function"
dict['fucntison']="function"
dict['fun()']="function ()"

IFS='%'  # keep whitespace and indentations
while read -r line; do
  for k in "${!dict[@]}"; do
    line="${line//$k/${dict[$k]}}"
  done
  echo "$line"
done < "${1:-/dev/stdin}" # read stdin or from a file
```

## Visualize

![bash-stdin-or-file-as-input.gif](bash-stdin-or-file-as-input.gif)
