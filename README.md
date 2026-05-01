# vboot
Modified Ventoy, a bootloader with no partition restrictions and flexible usage, UEFI version only.

## build

```
# build for x86_64-efi
echo '======== build grub2 for x86_64-efi ==============='
make distclean
./autogen.sh
./configure  --with-platform=efi --prefix=../../INSTALL/
make -j 16 || exit 1
sh install.sh  uefi


#build for i386-efi
echo '======== build grub2 for i386-efi ==============='
make distclean
./autogen.sh
./configure --target=i386 --with-platform=efi  --prefix=../../INSTALL/
make -j 16 || exit 1
sh install.sh  i386efi
```

## get grub.efi

```
./grub-mkimage -d ./grub-core -O x86_64-efi -o grubx64.efi \
  part_gpt part_msdos fat ext2 normal configfile search linux
```

or

```
./grub-mkstandalone -O x86_64-efi -o grub.efi

```