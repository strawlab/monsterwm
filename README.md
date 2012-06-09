monsterwm
=========

→ tiny and monsterous!
----------------------

**monsterwm** is a minimal, lightweight, tiny but monsterous dynamic tiling window manager.
It will try to stay as small as possible. Currently under 750 lines with the config file included.
It provides a set of different layout modes (see below), including floating mode support.
Each virtual desktop has its own properties, unaffected by other desktops' settings.
For screenshots and ramblings/updates check the [topic on ArchLinux forums][monsterwm].

  [monsterwm]: https://bbs.archlinux.org/viewtopic.php?id=132122


Modes
-----

Monsterwm allows opening the new window as master or
opening the window at the bottom of the stack (attach\_aside)

---

*Common tiling mode:*

    --------------
    |        | W |
    |        |___|
    | Master |   |
    |        |___|
    |        |   |
    --------------

---

*Bottom Stack (bstack) tiling mode:*

    -------------
    |           |
    |  Master   |
    |-----------|
    | W |   |   |
    -------------

---

 *Grid tiling mode:*

    -------------
    |   |   |   |
    |---|---|---|
    |   |   |   |
    |---|---|---|
    |   |   |   |
    -------------

one can have as many windows he wants.
`GRID` layout automatically manages the rows and columns.

---

 *Monocle mode* (aka fullscreen)

    -------------
    |           |
    | no        |
    | borders!  |
    |           |
    -------------

`MONOCLE` layout presents one window at a time in fullscreen mode.
Windows have no borders on this layout to save space.
See the `monocleborders` branch to give those windows borders.

---

 *floating mode*

    -------------
    |  |        |
    |--'  .---. |
    |     |   | |
    |     |   | |
    ------`---'--

 In floating mode one can freely move and resize windows in the screen space.
 Changing desktops, adding or removing floating windows, does not affect the
 floating status of the windows. Windows will revert to their tiling mode
 position once the user selects a tiling mode.
 To enter the floating mode, either change the layout to `FLOAT`, or
 enabled it by moving or resizing a window with the mouse, the window
 is then marked as being in floating mode.

---

All shortcuts are accessible via the keyboard and the mouse, and defined in `config.h` file.

All desktops store their settings independently.

 * The window W at the top of the stack can be resized on a per desktop basis.
 * Changing a tiling mode or window size on one desktop doesn't affect the other desktops.
 * toggling the panel in one desktop does not affect the state of the panel in other desktops.


Panel - Statusbar
-----------------

The user can define an empty space (by default 18px) on the bottom or top(default) of the
screen, to be used by a panel. The panel is toggleable, but will be visible if no windows
are on the screen.

Monsterwm does not provide a panel and/or statusbar itself. Instead it adheres
to the [UNIX philosophy][unix] and outputs information about the existent
desktop, the number of windows on each, the mode of each desktop, the current
desktop and urgent hints whenever needed. The user can use whatever tool or
panel suits him best (dzen2, conky, w/e), to process and display that information.

To disable the panel completely set `PANEL_HEIGHT` to zero `0`.
The `SHOW_PANELL` setting controls whether the panel is visible on startup,
it does not control whether there is a panel or not.

  [unix]: http://en.wikipedia.org/wiki/Unix_philosophy


Installation
------------

You need Xlib, then,
copy `config.def.h` as `config.h`
and edit to suit your needs.
Build and install.

    $ cp config.def.h config.h
    $ $EDITOR config.h
    $ make
    # make clean install


Patches
-------

Some extensions to the code are supported in the form of patches.
See other branches for the patch and code.
Easiest way to apply a patch, is to `git merge` that branch.

Currently:

 * [centerwindow]   : center new floating windows on the screen and  center any window with a shortcut
 * [fib]            : adds fibonacci layout mode
 * [initlayouts]    : define initial layouts for every desktop
 * [monocleborders] : adds borders to the monocle layout
 * [nmaster]        : adds nmaster layout - multiple master windows for BSTACK and TILE layouts
 * [showhide]       : adds a function to show and hide all windows on all desktops
 * [uselessgaps]    : adds gaps around every window on screen
 * [warpcursor]     : cursors follows and is placed in the center of the current window
 * [windowtitles]   : along with the rest desktop info, output the title of the current window

  [centerwindow]:   https://github.com/c00kiemon5ter/monsterwm/tree/centerwindow
  [fib]:            https://github.com/c00kiemon5ter/monsterwm/tree/fib
  [initlayouts]:    https://github.com/c00kiemon5ter/monsterwm/tree/initlayouts
  [monocleborders]: https://github.com/c00kiemon5ter/monsterwm/tree/monocleborders
  [nmaster]:        https://github.com/c00kiemon5ter/monsterwm/tree/nmaster
  [showhide]:       https://github.com/c00kiemon5ter/monsterwm/tree/showhide
  [uselessgaps]:    https://github.com/c00kiemon5ter/monsterwm/tree/uselessgaps
  [warpcursor]:     https://github.com/c00kiemon5ter/monsterwm/tree/warpcursor
  [windowtitles]:   https://github.com/c00kiemon5ter/monsterwm/tree/windowtitles

There is also another branch, called [`core`].
`core` is an even more stripped and minimal version of `monsterwm`,
on top of which the `master` branch is built and builds.

  [core]: https://github.com/c00kiemon5ter/monsterwm/tree/core

[Cloudef] has developed a [multi-monitor] version of monsterwm.
The [multi-monitor][mm] branch here is ideas and patches to Cloudef's work.
If you need multi-monitor support, grab his [multi-monitor] branch.

  Cloudef:        https://github.com/Cloudef
  multi-monitor:  https://github.com/Cloudef/monsterwm/tree/multi-monitor
  mm:             https://github.com/c00kiemon5ter/monsterwm/tree/multi-monitor

Bugs
----

For any bug or request [fill an issue][bug] on [GitHub][ghp] or report on the [ArchLinux topic][monsterwm]

  [bug]: https://github.com/c00kiemon5ter/monsterwm/issues
  [ghp]: https://github.com/c00kiemon5ter/monsterwm


License
-------

Licensed under MIT/X Consortium License, see [LICENSE][law] file for more copyright and license information.

  [law]: https://raw.github.com/c00kiemon5ter/monsterwm/master/LICENSE

Thanks
------

[the suckless team][skls] for [dwm][],
[moetunes][] for [dminiwm][],
[pyknite][] for [catwm][]

  [skls]: http://suckless.org/
  [dwm]:  http://dwm.suckless.org/
  [moetunes]: https://github.com/moetunes
  [dminiwm]:  https://bbs.archlinux.org/viewtopic.php?id=126463
  [pyknite]: https://github.com/pyknite
  [catwm]:   https://github.com/pyknite/catwm

