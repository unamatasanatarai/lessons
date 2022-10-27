# Trim whitespace in bash (ltrim, rtrim, trim)

Bash expansion to trim whitespace

## Trimming script

copy&paste the below snippets.

### Trim trailing whitespace

```
trim_trailing_whitespace() {
  echo "${1%"${1##*[![:space:]]}"}"
}
```

### Trim leading whitespace

```
trim_leading_whitespace() {
  echo "${1#"${1%%[![:space:]]*}"}"
}
```

### Trim whitespace

```
trim_whitespace() {
  : "${1#"${1%%[![:space:]]*}"}"
  echo "${_%"${_##*[![:space:]]}"}"
}
```


## How to integrate with VIM?

We will assume you have a script in your bash named `ttw` and in your $PATH and `chmod +x`'ed

```bash
#!/usr/bin/env bash
# ttw
trim_trailing_whitespace() {
  echo "${1%"${1##*[![:space:]]}"}"
}

while IFS= read -r line; do
  trim_trailing_whitespace "${line%"${line##*[![:space:]]}"}"
done < "${1:-/dev/stdin}"
```

### trim one/many lines

Use the !! from inside VIM on selected lines and enter `ttw`

### Trim whole file with keyboard shortcut

```nvim
keymap("n", "<leader>ss", ":%!ttw<cr>", opts)
-- or to save and restore your cursor position
keymap("n", "<leader>ss", ":norm mm<cr> | :execute '%!ttw'<cr> | :norm `m<cr>", opts)
```

### Trim whole file just before save

```nvim
autocmd("BufWritePre", {
  group = augroup,
  callback = function()
    vim.cmd ":norm mm"
    vim.cmd ":%!ttw"
    vim.cmd ":norm `m"
  end
})
```
