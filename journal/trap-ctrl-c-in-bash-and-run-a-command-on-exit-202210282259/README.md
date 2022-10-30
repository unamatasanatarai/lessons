# Trap ctrl+c in bash and run a command on exit

You can trap a signal. 

For ctrl+c the signal is `INT`

remember to `exit` after you catch the signal, otherwise you will block the exit

## implementation

### oneliner

```bash
# restore cursor to visible and exit
trap "tput cnorm; exit" INT
```

### function delegate

```bash
# restore cursor to visible and exit
trap x INT

x() {
  echo "Exiting"
  exit
}
```
