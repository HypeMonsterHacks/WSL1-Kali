# WSL1-Kali
Documentation related to installing WSL1 Kali on Windows 10.

Bugs encountered during install:

    libc-bin: Depends: libc6 (< 2.31) but 2.31-2 is to be installed

Explanation:

The current WSL1 Kali Linux implementation was built and compiled with important missing functionality. It seems most installs will fail when libc calls the nanosleep() function and looks for a non-existing POSIX clock "CLOCK_REALTIME".
Download the .deb file, reinstall libc6 2.31 using the following commands, and 'hold' the version so it is not auto-updated.


Fix:

`wget https://github.com/HypeMonsterHacks/WSL1-Kali/raw/master/libc6_2.31-0ubuntu8%2Blp1871129_1_amd64.deb`
`dpkg --install libc6_2.310ubuntu8+lp1871129~1_amd64.deb`  
`apt-mark hold libc6`  
`apt --fix-broken install`  
`apt full-upgrade`
