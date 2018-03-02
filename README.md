# Gentoo-Packer
Automated build for an image of Gentoo Linux

As part of a seperate project called PackerSystems (https://github.com/BaileyGingerTechnology/PackerSystems) I am using Packer to automate building a Gentoo workstation. That is going to intentionally be messed up, so I am making a copy of the files that build a clean version of Gentoo here for potential future use.

## How it works
The backbone of the build is a slightly edited version of my GentooInstall (https://github.com/BaileyGingerTechnology/GentooInstall) system. I make use of the Arch live CD for the pre-chroot portion, because for some reason SSH was not working for me with the Gentoo live CD.

System variables such as the country code are set inside the variables section of the gentoo.json file, rather than through user input like it would be normally. The system assumes English for locale, but that can be changed in the system_var_functions.sh file.

Expect the build to take several hours because of the kernel compile time. THe system could pretty easily be edited to make use of a .config file for that portion, but for now I am going to leave it using genkernel.

## Current Issues:
The install_mirrorselect.sh script fails because the disk runs out of space. I am probably going to have it hold off on installing that until mounting the drive and doing it there, or doing it post-build as a provisioner.