---
title: Switching from UNIX to Windows 11 (WSL2)
description: U++++>+++w-->+++@
layout: default
---

Forgive me for I hath sinned.

I've switched base OS from Linux LTS to Windows 11.

It's not as bad as you may think
\[[WSL2](https://learn.microsoft.com/en-us/windows/wsl/install) +
[debian](https://www.microsoft.com/en-us/search/shop/apps?q=linux),
[native X11](https://learn.microsoft.com/en-us/windows/wsl/tutorials/gui-apps),
shared [wslenv](https://devblogs.microsoft.com/commandline/share-environment-vars-between-wsl-and-windows/),
[cuda-wsl](https://docs.nvidia.com/cuda/wsl-user-guide/index.html),
[docker-wsl](https://docs.docker.com/desktop/windows/wsl),
[vscode-wsl](https://code.visualstudio.com/blogs/2020/07/01/containers-wsl),
[WSA](https://learn.microsoft.com/en-us/windows/android/wsa/)(!),
native monitor [calibration](https://www.tomshardware.com/how-to/calibrate-your-screen-windows-11) +
[inversion](https://support.microsoft.com/en-gb/windows/use-color-filters-in-windows-43893e44-b8b3-2e27-1a29-b0c15ef0e5ce#PickTab=Windows_11&WindowsVersion=Windows_11) +
[text superres](https://learn.microsoft.com/en-us/typography/cleartype/)\].

Also combining win + linux commands.

Windows running Linux:

```ps
PS C:\Users\Casper> wsl ls -l | wsl grep " -> " | Select-Object -First 1
lrwxrwxrwx 1 cas cas    35 Sep 30 17:03 Application Data -> /mnt/c/Users/Casper/AppData/Roaming
```

Linux running Windows:

```bash
~$ which winget.exe
/mnt/c/Users/Casper/AppData/Local/Microsoft/WindowsApps/winget.exe
```

Also bonus OEM [battery charge limits](https://www.asus.com/us/support/FAQ/1032726/) +
[AI noise cancellation](https://www.asus.com/support/FAQ/1044576/) +
less reliance on [hacks](https://github.com/pwr-Solaar/Solaar).

And companies actually fix even my most obscure esoteric issues (my AMD CPU has a built-in low-power GPU):\
![]({{ site.image_host }}/amd-driver-patch.jpg)

Finally, MS [PowerToys](https://learn.microsoft.com/en-gb/windows/powertoys):

-   [text-extractor](https://learn.microsoft.com/en-gb/windows/powertoys/text-extractor) to OCR literally anything
-   [always-on-top](https://learn.microsoft.com/en-gb/windows/powertoys/always-on-top) from Linux
-   no need for screenshots+image editors:

    -   [color-picker](https://learn.microsoft.com/en-gb/windows/powertoys/color-picker) to get hex codes
    -   [screen-ruler](https://learn.microsoft.com/en-gb/windows/powertoys/screen-ruler) to measure pixels

-   [file-explorer add-ons](https://learn.microsoft.com/en-gb/windows/powertoys/file-explorer) to preview `*.md`, `*.pdf`, ...
-   [keyboard-manager](https://learn.microsoft.com/en-gb/windows/powertoys/keyboard-manager) easier remapping
-   [powerrename](https://learn.microsoft.com/en-gb/windows/powertoys/powerrename) replacing my old trusty Python regex-based bulk file renaming script
-   [run](https://learn.microsoft.com/en-gb/windows/powertoys/run) like *HUD* in Linux or *Spotlight* on Mac

The only real cons so far are minor; I'm willing to live with them:

-   [lack of full unified memory support](https://docs.nvidia.com/cuda/wsl-user-guide/index.html#known-limitations-for-linux-cuda-apps)
-   [taskbar unlocking](https://techcommunity.microsoft.com/t5/windows-insider-program/windows-11-22533-breaks-taskbar-positioning/td-p/3062953)
-   [AppData indirects](https://support.mozilla.org/en-US/kb/profiles-where-firefox-stores-user-data/discuss/10897)
-   [virus false positives](https://community.harness.io/t/duplicate-virus-total-rating-as-tmate-as-trojan-malware/12292) (win-defender scans linux mounts lol)
-   common utils like [`file`](https://en.wikipedia.org/wiki/File_(command)) need manual `apt` installation
-   [conflicting updates](https://www.amd.com/en/support/kb/faq/pa-300) between [msstore](https://apps.microsoft.com/store/apps)-vs-[winget](https://github.com/microsoft/winget-cli)-vs-windows update-vs-OEM updater
-   [lack of X11 fonts support](https://github.com/microsoft/wslg/issues/310)
-   not-quite fully compliant WSL shell utils:

    ```bash
    ~$ cat ./-
    cat: ./-: No such file or directory
    ~$ echo foo | tee -
    foo
    ~$ echo bar | cat -
    bar
    ~$ echo bar | cat ./-
    foo
    ```

-   difficulty selecting text (only [some apps have work-arounds](http://kb.mozillazine.org/Layout.word_select.eat_space_to_next_word))
-   select-copy & middle-click-paste [isn't a thing](https://answers.microsoft.com/en-us/windows/forum/all/selection-into-clipboard-and-middle-mouse-button/fc65a0a8-34f2-43b1-bbbf-e29b2b699eb9)
-   [pro: there are lots of nice keyboard shortcuts. con: they keep changing between windows versions](https://support.microsoft.com/en-us/windows/keyboard-shortcuts-in-windows-dcc61a57-8ff0-cffe-9796-cb9706c75eec)

Haven't found any comprehensive guides online from 'nix powerusers taking win seriously (e.g. [this](https://adamtheautomator.com/windows-subsystem-for-linux/) has surprisingly little info).

idk if I should write a post about this - "Why I switched to Windows after 2 decades of Linux" [U++++\>+++w\--\>+++@](https://manpages.ubuntu.com/manpages/bionic/man1/geekcode.1.html)

even the surprisingly performant IDE tech stack is worth an under-the-hood exposition (vscode -\> containers extension -\> docker -\> wsl driver -\> mounted virtual disk).
