+++
title = "Useful key binding"
author = ["Hyosang Kim"]
date = 2018-09-06T11:03:00+09:00
lastmod = 2018-10-11T15:23:12+09:00
tags = ["post"]
draft = false
summary = "익혀두면 머리가 편해지는 단축키들"
+++

<div class="ox-hugo-toc toc">
<div></div>

<div class="heading">Table of Contents</div>

- [<B> Emacs (w/Spacemacs) </B>](#)
- [<B> Multi-session </B>](#)

</div>
<!--endtoc-->


## <B> Emacs (w/Spacemacs) </B> {#}

1.  Source Natvigation

    <div class="ox-hugo-table bind-key-table">
    <div></div>

    | Key Seq.    | func.              | alter     | comments                      |
    |-------------|--------------------|-----------|-------------------------------|
    | `SPC j i`   | symbol jump        | `SPC s j` | imenu-list 보다 쓰기 편하네, SPC b i |
    | `SPC p f`   | find file in prj.  |           | projectile 내에서             |
    |             | compilation-mode   |           | <M-n>,<M-p> search errors     |
    | `C-x r m`   | set bookmark       | `SPC f b` | set bookmark and jump to      |
    | `SPC m g a` | open matching file |           | switch .cpp and .h            |

    </div>

    tips:<br>
    compilation-mode : add user config "(setq compilation-skip-threshold 2)" <br>
                       // only for errors navigation
2.  Layout

    <div class="ox-hugo-table bind-key-table">
    <div></div>

    | Key Seq. | func.             | alter   | add key       |
    |----------|-------------------|---------|---------------|
    | `SPC l`  | Layout management | `M-m l` | w : Workspace |

    </div>

    1.  basic

    <div class="ox-hugo-table bind-key-table">
    <div></div>

    | Key Seq.  | func.               | alter | add key       |
    |-----------|---------------------|-------|---------------|
    | `SPC r y` | helm-show-kill-ring | `M-w` | show and save |

    </div>


## <B> Multi-session </B> {#}

1.  Tmux
2.  screen
