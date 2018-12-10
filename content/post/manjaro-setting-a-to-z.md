+++
title = "Manjaro Setting"
author = ["Hyosang Kim"]
date = 2018-12-08T18:24:00+09:00
lastmod = 2018-12-10T14:08:39+09:00
tags = ["post"]
draft = true
summary = "summary"
+++

<div class="ox-hugo-toc toc">
<div></div>

<div class="heading">Table of Contents</div>

- [Base setup](#base-setup)
- [Setting](#setting)
- [Packages install](#packages-install)
- [VNC 관련](#vnc-관련)

</div>
<!--endtoc-->

   Manjaro는 킬리만자로에서 따왔다고 한다. 만자로 혹은 만하로라고 불리운다.
   Odroid XU3에서 사용했었는데, x86기반 SBC를 알아보다 Odroid H2로 결정.<br>
   아래는 Odroid H2에 manjaro를 설치하면서 정리한 내용이다.
<br>


## Base setup {#base-setup}

빠른 업데이트를 위해서 할것들

-   Time :

```shell
sudo timedatectl set-ntp true
```

-   Networks : [jumboframe](https://wiki.archlinux.org/index.php/jumbo%5Fframes) 설정 (공유기나 허브가 지원하는지 부터 확인)
-   repositories :

```shell
sudo pacman-mirrors -f0 # 시간이 꽤 걸림
```

-   fast build :
    업데이트 하면서 소스 빌드도 하기 때문에 멀티코어 사용자라면 <br> 자신의 코어수 +1로 설정하면 빌드 시간이 빨라진다.

/etc/makepkg.conf 파일에서 MAKEFLAGS="-j5" 뒤에 숫자만 수정하면 된다.

-   update : 아래 명령어로 업데이트 하고서 느긋하게 기다리자.

```shell
sudo pacman -Syyu
```

<br>


## Setting {#setting}

-   SSD (Disable Continuous Trim for SSD Drivers)

```shell
sudo systemctl enable fstrim.timer
```

-   [watchdog](https://www.jann.cc/2013/02/02/linux%5Fwatchdog.html) enable : 원격 사용자라면 WOL과 함께 필수일듯~
-   NAS mount : /etc/fstab 에 쓰고, sudo mount -a 하면 됨.

```text
serverIP:directory local_directory nfs auto,nofail,noatime,nolock,intr,tcp,actimeo=1800 0 0
```

-   NAS 설정후 터미널에서 디렉토리 색상이 마음에 들지 않을때.
    home 디렉토리에 .bashrc파일에 eval "$(dircolors ~/.dircolors)"
    그리고 .dircolors 파일을 생성후 아래 내용 적은후 로그인 새로하거나 업데이트 하거나
    '#' 이후는 주석, 자세한 내용은 [dircolors](https://unix.stackexchange.com/questions/94498/what-causes-this-green-background-in-ls-output) 참고

```text
STICKY_OTHER_WRITABLE 30;40 # dir that is sticky and other-writable (+t,o+w)
OTHER_WRITABLE 34;40 # dir that is other-writable (o+w) and not sticky
```

<br>


## Packages install {#packages-install}

-   환경 설정 관련은 모두 [Dropbox](https://www.unixmen.com/install-dropbox-manjaro-xfce-arch-linux/) 에 있고 링크만 걸어서 사용한다.

```shell
sudo pacman -S yaourt emacs vim screen tmux pandoc git wget hugo npm fzf bzip2
yaourt -S google-chrome ttf-d2coding noto-fonts-cjk ttf-nanum
yaourt -S zsh zsh-completions zsh-theme-powerlevel9k
```

-   google drive 사용은 [rclone](https://rclone.org/commands/rclone%5Fmount/) 으로 결정.
-   spacemacs (ln dotspacemacs ,ln private), install [tern](https://blog.nacyot.com/articles/2014-03-12-emacs-with-tern/)
-   screen, tmux (ln tmux.conf,[tmux-powerline](https://github.com/erikw/tmux-powerline))
-   zsh & oh-my-zsh & [powerlevel9k](https://github.com/bhilburn/powerlevel9k/wiki/Stylizing-Your-Prompt)

```shell
yaourt -S zsh zsh-completions
git clone git://github.com/robbyrussell/oh-my-zsh.git ~/.oh-my-zsh
yaourt -S zsh-theme-powerlevel9k
```

<br>


## VNC 관련 {#vnc-관련}

-   접속 pc종류가 많을땐 vnc해상도가 골치이다. 그래서 xrandr([2560x1080](https://forum.manjaro.org/t/solved-unable-to-set-2560x1080-on-external-display/34247/11)) 을 이용하면 편하다.
    서버에서 geometry설정 하는것 보다는 이방식이 더 낫다. VNC-0 인지는 확인해보고 할것.
-   server [VNC](https://www.addictivetips.com/ubuntu-linux-tips/set-up-vnc-desktop-sharing-on-linux-with-tigervnc/) ,로컬은 [tightVNC](https://superuser.com/questions/540103/tightvnc-cannot-exit-full-screen-in-windows-7) 그리고 로컬이 윈도우인경우는 [multidesktop](https://virtuawin.sourceforge.io/) 을 사용한다.

```shell
#!/bin/sh
xrandr --newmode "2560x1080" 185.58 2560 2624 2688 2784 1080 1083 1093 1111 -HSync -VSync
xrandr --addmode VNC-0 2560x1080
xrandr --output VNC-0 --mode 2560x1080
```
