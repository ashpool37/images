# `guestfs-tools` &mdash; inspect and modify VM images.

A Fedora-based image containing `guestfs-tools` and it dependencies.

The binaries are run as a non-root user inside the container, so privilege mapping is necessary. `--userns=keep-id` works with Podman.

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
