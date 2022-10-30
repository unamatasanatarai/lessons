# How do I capture stderr in bash into variable

Take a look at my "rec" script in the [dotfiles](https://github.com/unamatasanatarai/dotfiles/blob/master/stow/bin/rec). Asciinema prints the uploaded URL into stderr. 

## how to capture it:

```
$ response=$(asciinema upload filename.cast 2>&1)
$ echo $response
```
