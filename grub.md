### grub配置
```
#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s $prefix/grubenv ]; then
  load_env
fi
set default="0"

if [ x"${feature_menuentry_id}" = xy ]; then
  menuentry_id_option="--id"
else
  menuentry_id_option=""
fi

export menuentry_id_option

if [ "${prev_saved_entry}" ]; then
  set saved_entry="${prev_saved_entry}"
  save_env saved_entry
  set prev_saved_entry=
  save_env prev_saved_entry
  set boot_once=true
fi

function savedefault {
  if [ -z "${boot_once}" ]; then
    saved_entry="${chosen}"
    save_env saved_entry
  fi
}

function load_video {
  if [ x$feature_all_video_module = xy ]; then
    insmod all_video
  else
    insmod efi_gop
    insmod efi_uga
    insmod ieee1275_fb
    insmod vbe
    insmod vga
    insmod video_bochs
    insmod video_cirrus
  fi
}

if [ x$feature_default_font_path = xy ] ; then
   font=dejavusansmono
else
insmod part_msdos
insmod ext2
set root='hd0,msdos3'
if [ x$feature_platform_search_hint = xy ]; then
  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos3 --hint-efi=hd0,msdos3 --hint-baremetal=ahci0,msdos3  178a7a85-b573-493b-af62-3d00149f3658
else
  search --no-floppy --fs-uuid --set=root 178a7a85-b573-493b-af62-3d00149f3658
fi
    font="/usr/share/grub/dejavusansmono.pf2"
fi

if loadfont $font ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
  set locale_dir=$prefix/locale
  set lang=en_US
  insmod gettext
fi
terminal_output gfxterm
set timeout=10
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/10_linux ###
menuentry 'Slackware-14.2 GNU/Linux' --class slackware-14.2 --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-simple-178a7a85-b573-493b-af62-3d00149f3658' {
	load_video
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='hd0,msdos2'
	if [ x$feature_platform_search_hint = xy ]; then
	  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos2 --hint-efi=hd0,msdos2 --hint-baremetal=ahci0,msdos2  75d5b1de-3fe5-402e-a8e7-aa44aec5dd46
	else
	  search --no-floppy --fs-uuid --set=root 75d5b1de-3fe5-402e-a8e7-aa44aec5dd46
	fi
	echo	'Loading Linux 4.4.14 ...'
	linux	/vmlinuz-huge-4.4.14 root=/dev/sda3 ro  
}
submenu 'Advanced options for Slackware-14.2 GNU/Linux' $menuentry_id_option 'gnulinux-advanced-178a7a85-b573-493b-af62-3d00149f3658' {
	menuentry 'Slackware-14.2 GNU/Linux, with Linux 4.4.14' --class slackware-14.2 --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-4.4.14-advanced-178a7a85-b573-493b-af62-3d00149f3658' {
		load_video
		insmod gzio
		insmod part_msdos
		insmod ext2
		set root='hd0,msdos2'
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos2 --hint-efi=hd0,msdos2 --hint-baremetal=ahci0,msdos2  75d5b1de-3fe5-402e-a8e7-aa44aec5dd46
		else
		  search --no-floppy --fs-uuid --set=root 75d5b1de-3fe5-402e-a8e7-aa44aec5dd46
		fi
		echo	'Loading Linux 4.4.14 ...'
		linux	/vmlinuz-huge-4.4.14 root=/dev/sda3 ro  
	}
	menuentry 'Slackware-14.2 GNU/Linux, with Linux 4.4.14 (recovery mode)' --class slackware-14.2 --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-4.4.14-recovery-178a7a85-b573-493b-af62-3d00149f3658' {
		load_video
		insmod gzio
		insmod part_msdos
		insmod ext2
		set root='hd0,msdos2'
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos2 --hint-efi=hd0,msdos2 --hint-baremetal=ahci0,msdos2  75d5b1de-3fe5-402e-a8e7-aa44aec5dd46
		else
		  search --no-floppy --fs-uuid --set=root 75d5b1de-3fe5-402e-a8e7-aa44aec5dd46
		fi
		echo	'Loading Linux 4.4.14 ...'
		linux	/vmlinuz-huge-4.4.14 root=/dev/sda3 ro single 
	}
	menuentry 'Slackware-14.2 GNU/Linux, with Linux huge' --class slackware-14.2 --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-huge-advanced-178a7a85-b573-493b-af62-3d00149f3658' {
		load_video
		insmod gzio
		insmod part_msdos
		insmod ext2
		set root='hd0,msdos2'
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos2 --hint-efi=hd0,msdos2 --hint-baremetal=ahci0,msdos2  75d5b1de-3fe5-402e-a8e7-aa44aec5dd46
		else
		  search --no-floppy --fs-uuid --set=root 75d5b1de-3fe5-402e-a8e7-aa44aec5dd46
		fi
		echo	'Loading Linux huge ...'
		linux	/vmlinuz-huge root=/dev/sda3 ro  
	}
	menuentry 'Slackware-14.2 GNU/Linux, with Linux huge (recovery mode)' --class slackware-14.2 --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-huge-recovery-178a7a85-b573-493b-af62-3d00149f3658' {
		load_video
		insmod gzio
		insmod part_msdos
		insmod ext2
		set root='hd0,msdos2'
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos2 --hint-efi=hd0,msdos2 --hint-baremetal=ahci0,msdos2  75d5b1de-3fe5-402e-a8e7-aa44aec5dd46
		else
		  search --no-floppy --fs-uuid --set=root 75d5b1de-3fe5-402e-a8e7-aa44aec5dd46
		fi
		echo	'Loading Linux huge ...'
		linux	/vmlinuz-huge root=/dev/sda3 ro single 
	}
	menuentry 'Slackware-14.2 GNU/Linux, with Linux 4.4.14' --class slackware-14.2 --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-4.4.14-advanced-178a7a85-b573-493b-af62-3d00149f3658' {
		load_video
		insmod gzio
		insmod part_msdos
		insmod ext2
		set root='hd0,msdos2'
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos2 --hint-efi=hd0,msdos2 --hint-baremetal=ahci0,msdos2  75d5b1de-3fe5-402e-a8e7-aa44aec5dd46
		else
		  search --no-floppy --fs-uuid --set=root 75d5b1de-3fe5-402e-a8e7-aa44aec5dd46
		fi
		echo	'Loading Linux 4.4.14 ...'
		linux	/vmlinuz-generic-4.4.14 root=/dev/sda3 ro  
	}
	menuentry 'Slackware-14.2 GNU/Linux, with Linux 4.4.14 (recovery mode)' --class slackware-14.2 --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-4.4.14-recovery-178a7a85-b573-493b-af62-3d00149f3658' {
		load_video
		insmod gzio
		insmod part_msdos
		insmod ext2
		set root='hd0,msdos2'
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos2 --hint-efi=hd0,msdos2 --hint-baremetal=ahci0,msdos2  75d5b1de-3fe5-402e-a8e7-aa44aec5dd46
		else
		  search --no-floppy --fs-uuid --set=root 75d5b1de-3fe5-402e-a8e7-aa44aec5dd46
		fi
		echo	'Loading Linux 4.4.14 ...'
		linux	/vmlinuz-generic-4.4.14 root=/dev/sda3 ro single 
	}
	menuentry 'Slackware-14.2 GNU/Linux, with Linux generic' --class slackware-14.2 --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-generic-advanced-178a7a85-b573-493b-af62-3d00149f3658' {
		load_video
		insmod gzio
		insmod part_msdos
		insmod ext2
		set root='hd0,msdos2'
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos2 --hint-efi=hd0,msdos2 --hint-baremetal=ahci0,msdos2  75d5b1de-3fe5-402e-a8e7-aa44aec5dd46
		else
		  search --no-floppy --fs-uuid --set=root 75d5b1de-3fe5-402e-a8e7-aa44aec5dd46
		fi
		echo	'Loading Linux generic ...'
		linux	/vmlinuz-generic root=/dev/sda3 ro  
	}
	menuentry 'Slackware-14.2 GNU/Linux, with Linux generic (recovery mode)' --class slackware-14.2 --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-generic-recovery-178a7a85-b573-493b-af62-3d00149f3658' {
		load_video
		insmod gzio
		insmod part_msdos
		insmod ext2
		set root='hd0,msdos2'
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos2 --hint-efi=hd0,msdos2 --hint-baremetal=ahci0,msdos2  75d5b1de-3fe5-402e-a8e7-aa44aec5dd46
		else
		  search --no-floppy --fs-uuid --set=root 75d5b1de-3fe5-402e-a8e7-aa44aec5dd46
		fi
		echo	'Loading Linux generic ...'
		linux	/vmlinuz-generic root=/dev/sda3 ro single 
	}
}

### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry 'Windows 7 (loader) (on /dev/sda1)' --class windows --class os $menuentry_id_option 'osprober-chain-9656A06156A04439' {
	insmod part_msdos
	insmod ntfs
	set root='hd0,msdos1'
	if [ x$feature_platform_search_hint = xy ]; then
	  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos1 --hint-efi=hd0,msdos1 --hint-baremetal=ahci0,msdos1  9656A06156A04439
	else
	  search --no-floppy --fs-uuid --set=root 9656A06156A04439
	fi
	chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

### BEGIN /etc/grub.d/41_custom ###
if [ -f  ${config_directory}/custom.cfg ]; then
  source ${config_directory}/custom.cfg
elif [ -z "${config_directory}" -a -f  $prefix/custom.cfg ]; then
  source $prefix/custom.cfg;
fi
### END /etc/grub.d/41_custom ###
```
