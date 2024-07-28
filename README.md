# cntg_lpic_vagrantfile_para_m2
Vagrantfile para empregar en chips Apple M2 para crear máquinas virtuais empregadas no LPIC-2 do CNTG

## Requerimentos

Ter instalado `qemu` e/ou `libvirt` (empregar `Homebrew`, por exemplo) e `vagrant-qemu` (plugin de vagrant)


## Know issues

- Non se poden empregar configs de rede, por exemplo a que quere definir a IP, por falta de soporte no `vagrant-qemu` (https://github.com/ppggff/vagrant-qemu?tab=readme-ov-file#todo):

```bash
==> centos72: Warning! The QEMU provider doesn't support any of the Vagrant
==> centos72: high-level network configurations (`config.vm.network`). They
==> centos72: will be silently ignored.
```