# WSL2 Kernel CI

Github Actions CI config for WSL2 Kernel.

## What's This?

- Source code is from apt source linux, necessary config for WSL (Mainly from [this commit](https://github.com/microsoft/WSL2-Linux-Kernel/commit/65efab378febd57f3fd10bba40c37a0f269b6f69)) is added.
- You can install kernel header and loadable modules with linux-headers and linux-modules{-extra}, need to umount /lib/modules first.
- Create a script named `/etc/kernel/postinst.d/copy-to-windows` to let ubuntu auto update kernel binary
  ```bash
  #!/bin/sh
  if [ ! -d /mnt/c/WSL ]; then
      mkdir /mnt/c/WSL
  fi
  cp /boot/vmlinuz /mnt/c/WSL/bzImage
  ```
- Dxgkrnl patch is not added and can be installed as a [dkms module](https://github.com/staralt/dxgkrnl-dkms).  


Enjoy it!

---
**Notes: I don't make a change in version string, so mark these packages as hold to avoid auto update.**
