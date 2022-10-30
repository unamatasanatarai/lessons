# Bash dollar singlequote is escaped

No longer must you use `echo -e`.

try this:

```
$ echo $'to the left\tafter tab\nnew line'

to the left	after tab
new line
```

HOWEver... it must be singlequotes, ...so variables?
