# Podman basic instructions

## First things first - a throwaway container

```
podman run -it --rm alpine /bin/sh
podman run -it --rm --rmi alpine /bin/sh
```

what?
- `podman run` - duh!
- `-it` - _interactive_
  - `-i` - interactive
  - `-t` - start a tty
- `--rm` - remove the container after exit. i.e. _cleanup_
- `--rmi` - remove the image after exit. i.e. _cleanup_ and always download a fresh image
- `alpine` - small footprint image

## First, create the machine!

If no name is specified, then the default name is `podman-default-machine`

```console
$ podman machine init
$ podman machine list
NAME                     VM TYPE     CREATED             LAST UP             CPUS        MEMORY      DISK SIZE
podman-machine-default*  qemu        About a minute ago  About a minute ago  1           2.147GB     107.4GB
```

```console
$ podman machine init nomenomen
$ podman machine list
NAME                     VM TYPE     CREATED         LAST UP         CPUS        MEMORY      DISK SIZE
nomenomen                qemu        43 seconds ago  43 seconds ago  1           2.147GB     107.4GB
podman-machine-default*  qemu        3 minutes ago   3 minutes ago   1           2.147GB     107.4GB
```

### Do I really need to give it a name?

Probably not. I don't know. For my needs, I do not.


## Second, start|stop the machine!

Start the default machine

```console
$ podman machine start
$ podman machine stop
```

Start the named machine

```console
$ podman machine start nomenomen
$ podman machine stop nomenomen
```

