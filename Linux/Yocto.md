# Table of Contents

- [Table of Contents](#table-of-contents)
  - [Bitbake commands](#bitbake-commands)
  - [Variables](#variables)

## Bitbake commands

https://community.nxp.com/docs/DOC-94953

Layers commands

```shell
bitbake layers
bitbake show-layers
bitbake-layers add-layer ../meta-clang
```

List all the targets/recipes/images:

```shell
bitbake-layers show-recipes
bitbake-layers show-recipes "*image*"
```

Compiling certain package:

```shell
bitbake -C compile virtual/bootloader
```

Configuring kernel:

```shell
bitbake -c menuconfig virtual/kernel
```

Download all sources for building package:

```shell
bitbake -c fetchall core-image-sato
```

Invoke clean task in recipe:

```shell
bitbake myrecipe -c clean
```

Building image with toolchain:

```shell
bitbake core-image-minimal -c populate_sdk
```

To find the build directory for package:

```shell
bitbake -e <package> | grep ^WORKDIR=
```

Where rootfs placed:

```shell
bitbake -e <package> | grep ^IMAGE_ROOTFS=
```

Turn on debug 3 levels deep:

```shell
bitbake -DDD core-image-minimal
```

Listing recipe versions:

```shell
bitbake -s
```

Examine the defined "tasks" for any target with:

```shell
bitbake -c listtasks strace
```

Rebuild kernel:

```shell
bitbake -c cleansstate linux-p5-on-wandboard
bitbake -f -c compile linux-p5-on-wandboard
bitbake -f -c deploy linux-p5-on-wandboard
```

## Variables

| Variable     | Description         |
| :----------- | ------------------- |
| B            | Build directory     |
| S            | Source directory    |
| WORKDIR      | Work directory      |
| IMAGE_ROOTFS | Where rootfs placed |
