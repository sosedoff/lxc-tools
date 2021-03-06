# lxc-tools

Set of tools to work with LXC containers and host system. 

Extracted from experimental scripts and currently under development.

## Requirements

- Ubuntu 11.04 / 11.10 64-bit system
- Superuser privileges (required in some scripts)
- Ruby 1.8.7 / 1.9.x

## Install

To install all utilities, run:

```
git clone https://github.com/sosedoff/lxc-tools.git
cd lxc-tools
rake install
```

All files will be installed under `/usr/local/bin` on your system.

## Tools

- `lxc-setup-network` - Setup and configure bridge interface for containers
- `lxc-setup-container` - Create and configure a new LXC container
- `lxc-setup-rootfs` - Create and configure rootfs for containers

## lxc-setup-network

This utility will create a new network interface `br0` for LXC containers. By default,
this bridge interface will be configured on `192.168.1.x` address space. 

Usage:

```
Usage: lxc-setup-network [options]
    -h, --help                       Display this information.
        --host INTERFACE             Host interface name
        --bridge INTERFACE           Bridge interface name
        --bridge-ip IP               Bridge interface IP address
```

Network configuration commands will be executed as sudo so make sure user has
a proper privileges.

## lxc-setup-rootfs

This utility will debootstrap a clean filesystem for LXC containers. Was only tested
on 64bit ubuntu 11.04/11.10 systems. Usage:

```
Usage: lxc-setup-rootfs [options]
    -h, --help                       Display this information.
        --variant NAME               Bootstrap variant. Default: minbase
        --components LIST            System components
        --packages LIST              List of packages to install
        --release NAME               Release name
        --arch ARCH                  Release architechture
        --path PATH                  Extract path
```

## lxc-setup-container

This utility will create and configure a new LXC container. Basic usage:

```
Usage: lxc-setup-container [options]
    -h, --help                       Display this information.
    -n, --name NAME                  Container name
    -p, --path PATH                  Mount path
        --rootfs PATH                Path to clean rootfs
        --memory MEGABYTES           Memory limit in megabytes
        --net-ip IP                  Assign IP address
        --net-gateway IP             Container gateway IP
        --net-mask MASK              Container netmask
```

Before using container setup tool you must have a source rootfs, which will be used
as a base for a new container. For more information check `lxc-setup-rootfs` utility.

It also requires a few ruby libraries before you can use it. Run:

```
gem instal terminal_helpers mustache
```

Execute as: 

```
lxc-setup-container --name app1 --rootfs /path --path /lxc/app1
```

## License

See LICENSE file for details
