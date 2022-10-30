# $CDPATH does what autojump and z does

`cd <enter>` automatically takes you to `~`.

Would it not be nice to jump to typical directories automatically also?

`*` important to always keep `.:` at the begining of CDPATH, otherwise you won't cd into anything.

## Implementation

```bash
#.bashrc, or .bash_profile
export CDPATH=".:~:~/dev"
```

