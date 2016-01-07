Building the PAM Module.

# Introduction #

The PAM Module has been successfully build and operated on AMDx86\_64
Compilation of the module requires the following packages:

**+**build-essential

**+**libpam0g-dev

**+**libcurl4-openssl-dev

# When Dependencies are Met #

Change the Working directory to where the module is located, then as "root" run the following commands:

gcc -fPIC -fno-stack-protector -lcurl -c google-pam.c

ld -lcurl -x --shared -o /lib/security/google-pam.so google-pam.o

# Enabling PAM Module #

Change your working directory to **/etc/pam.d**
as **root**, open the corresponding login file with your favorite text editor.

_example:_ sudo nano /etc/pam.d/lightdm

find the line which says "**@include common-auth**" and insert the following line directly above it:

auth sufficient google-pam.so

# Google Apps for Domain Test #

Note: Current Module does not allow for Apps accounts.
In the future you may use Google apps for domains; when calling the google-pam.so file in your PAM config it may be modified as follows:

auth sufficent google-pam.so _yourappsdomain.com_

_Replace "yourappsdomain.com" with Your Domain Name_