# How to replace regexp in bash

In just bash, set a flag:

`shopt -s extglob`

do what you need

`shopt -u extglob`

## example

```
bad="a,.!1234,,,,,,,,,,,,,,,,jb"
shopt -s extglob
good=${bad//+([^a-z0-9_-])/-}
shopt -u extglob

echo $bad
echo $good

# result:
a,.!1234,,,,,,,,,,,,,,,,jb
a-1234-jb
```

