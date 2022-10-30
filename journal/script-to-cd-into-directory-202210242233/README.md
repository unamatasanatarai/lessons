# How do I cd into a directory holding a file with a script?

- a bash function can do it
- an executable bash script cannot, it will only cd into a directory for itself and exit to where you were when done

## impl

1. run which
1. dirname the location
1. cd into the location
1. exit 1 on any error

```
wcd() {
  cd "$(dirname "$(which "$1")")" || return 1
}
```