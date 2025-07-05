# `guestfs-tools` &mdash; inspect and modify VM images.

A Fedora-based image containing `guestfs-tools` and its dependencies.

The binaries are run as a non-root user inside the container, so id mapping is necessary. `--userns=keep-id` works with Podman when running rootless. Use `--user 0:0` to run the binaries as root.

## Example usage

Run a `guestfish` interactive shell on a Ubuntu Noble cloud image in the current directory:

```sh
podman run -it -v "${PWD}/noble-server-cloudimg-amd64.img:/home/virt/guest.img" --userns=keep-id
```

Set a random root password for the image:

```sh
podman run -v "${PWD}/noble-server-cloudimg-amd64.img:/home/virt/guest.img" --userns=keep-id \
    virt-customize --root-password random
```
