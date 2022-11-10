# Vim Very Magic Regexp searching and replace (perl complient)

When I type into vim `:help magic`, vim's help spews out a lot of information, but very little of it is readable. Why!? Why aren't there any real life examples?

...anyway

To make use of Perl complient regex in vim, I need to make use of the `\v` switch, as shown in the following example:

```
:s/\v[a-z]+/-/g
```

![Vim Very Magic](vim-very-magic.gif)
[![asciicast](https://asciinema.org/a/536494.svg)](https://asciinema.org/a/536494)
