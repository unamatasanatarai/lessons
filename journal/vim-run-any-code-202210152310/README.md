# Run any code and read it back into vim

## Single line run

1. Type some code in VIM.
1. Place the cursor on the line of the code.
1. hit: bang bang `!!`
1. add `bash` and hit enter

**example**

```
for i in {6..9}; do echo "line #$i"; done
```

produces:

```
line #6
line #7
line #8
line #9
```

## Multiline execution


1. Type some code in VIM.
1. Place the cursor on the line of the code.
1. hit: bang ap `!ap`
1. add `bash` and hit enter

```
for i in {6..9}
  do echo "line #$i"
done
```

produces:

```
line #6
line #7
line #8
line #9
```


## Works with any language

try with:

```python
st="I am a python string"
print(f"Hello there! {st}")
```

1. shift+V select both lines
1. hit `!`
1. type `python3`
1. hit enter

## Visualized

![vim any language](vim-run-any-code.gif)

---
n'joy!