# Bash expanded dirname

A very simple solution: `"${0%/*}"`

[A highly robust solution](https://github.com/dylanaraps/pure-bash-bible#get-the-directory-name-of-a-file-path)

```bash
dirname() {
    # Usage: dirname "path"
    local tmp=${1:-.}

    [[ $tmp != *[!/]* ]] && {
        printf '/\n'
        return
    }

    tmp=${tmp%%"${tmp##*[!/]}"}

    [[ $tmp != */* ]] && {
        printf '.\n'
        return
    }

    tmp=${tmp%/*}
    tmp=${tmp%%"${tmp##*[!/]}"}

    printf '%s\n' "${tmp:-/}"
}
```
