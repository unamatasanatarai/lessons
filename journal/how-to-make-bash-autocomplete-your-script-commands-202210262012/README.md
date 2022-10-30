# How to make bash autocomplete your script commands

The following solution assumes:

- commands for your script are functions
- functions begining with `_` (underscore) are private functions and will not be suggested/autocompleted

# how to get autocomplete for bash

1. Setup bash to work with your script. For example:

```bash
$ complete -C cmpltn cmpltn
```

2. Add the below snippet at the bottom of your script

```bash
# ------------------------------- THE COMPLETION --------------------------------
declare -a functions=()
while IFS= read -r f; do
  [[ ${f:0:1} != "_" ]] && functions+=("$f")
done < <(compgen -A function)
if [[ -n ${COMP_LINE:-} ]]; then
  for cmd in "${functions[@]}"; do
    [[ ${cmd:0:${#2}} == "$2" ]] && echo "$cmd"
  done
fi
```


## demo

![how-to-make-bash-autocomplete-your-script-commands-20221026-2012.gif](how-to-make-bash-autocomplete-your-script-commands-20221026-2012.gif)
