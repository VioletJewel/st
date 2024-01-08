st - simple terminal
====================
st is a simple terminal emulator for X which sucks less.

See [suckless.org][0] for more info.

Violet's Patches
----------------

Yeah, it's basically my terminal and no one elses. You can't easily remove the
patches, so probably scurry along, curious browser. Nothing to see here.

- [scrollback][1]: add scrollback capabilities
  - scrollback: M-S-k, M-S-j to scroll
  - resizing reflows text
  - mouse wheel scrolls
- [ligatures][2]: ligature support
  - also using FiraCode Nerd Font for ligature support
- [bold-is-not-bright][3]: bold attribute doesn't use bright colors
- [anysize][4]: terminal doesn't enforce size (expected variant)
- [copyurl][5]: allows for copying urls to clipboard
  - M-u, M-S-u cycle forward, backward (resp.)
  - highlights the links and supports multiline links
- [open copied url][6]: opens the url from copyurl
  - M-Return to open the url with `xdg-open`
- [undercurl][7]: supports undercurl (ie, in nvim)
- [w3m][8]: w3mimg support for images (ie, in ranger with `review_images_method = w3m`)
- [autocomplete][9]: autocomplete words or fuzzily (or more if you want)
    - M-S-l, M-S-; complete word or fuzzyily
    - M-S-BackSpace reverts the completion back to the original text
- [dracula][10]: colorscheme

Violet's Keymaps
----------------

| Key | Description |
| --- | ----------- |
| C-S-= | Increase font size |
| C-S-- | Decrease font size |
| C-S-0 | Reset font size |
| C-S-c | Copy to Clipboard |
| C-S-v | Paste from Clipboard |
| C-S-y | Past from Selection (alt: S-Insert) |
| M-S-k | Scroll terminal up |
| M-S-j | Scroll terminal down |
| M-u   | Copy & highlight URLs cyclicly upwards from bottom |
| M-S-u | Copy & highlight URLs cyclicly downwards from top |
| M-Return | Open copied URL |
| M-S-l | Complete a partial word that is somewhere in the terminal buffer |
| M-S-; | Complete a fuzzy match of text in the terminal buffer |
| M-S-BackSpace | Undo the completion (revert to original text)  |

- C-S-{key} is Control + Shift + {key}
- M-{key} is Meta (Alt) + {key}
- M-S-{key} is Meta (Alt) + Shift + {key}

Violet's Notes
--------------

I use `rm -f config.h; make && sudo make install && make clean` after modifying
config.def.h; do whatever feels comfy, though, and don't remove config.h if it
has changes, obviously.

For undercurl support in tmux, add this to your .tmux.conf:

```
set -as terminal-overrides ',*:Smulx=\E[4::%p1%dm'  # undercurl support
set -as terminal-overrides ',*:Setulc=\E[58::2::%p1%{65536}%/%d::%p1%{256}%/%{255}%&%d::%p1%{255}%&%d%;m'  # underscore colours - needs tmux-3.0
```

Obviously, if you want ligatures, use a monospace font that supports ligatures.

Requirements
------------
In order to build st you need the Xlib header files.


Installation
------------
Edit config.mk to match your local setup (st is installed into
the /usr/local namespace by default).

Afterwards enter the following command to build and install st (if
necessary as root):

    make clean install


Running st
----------
If you did not install st with make clean install, you must compile
the st terminfo entry with the following command:

    tic -sx st.info

See the man page for additional details.

Credits
-------
Based on Aurélien APTEL <aurelien dot aptel at gmail dot com> bt source code.

[0]: https://st.suckless.org/ "suckless.org st - simple terminal"
[1]: https://st.suckless.org/patches/scrollback/ "simple terminal Scrollback patches"
[2]: https://st.suckless.org/patches/ligatures/ "simple terminal Ligature Support patch"
[3]: https://st.suckless.org/patches/bold-is-not-bright/ "simple terminal bold-is-not-bright patch"
[4]: https://st.suckless.org/patches/anysize/ "simple terminal anysize (expected variant) patch"
[5]: https://st.suckless.org/patches/copyurl/ "simple terminal copyurl patches"
[6]: https://st.suckless.org/patches/open_copied_url/ "suckless open copied url patch"
[7]: https://st.suckless.org/patches/undercurl/ "simple terminal undercurl patch"
[8]: https://st.suckless.org/patches/w3m/ "simple terminal w3m patch"
[9]: https://st.suckless.org/patches/autocomplete/ "simple terminal autocomplete patch"
[10]: https://st.suckless.org/patches/dracula/ "simple terminal dracula patch"
