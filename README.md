Lisp Machine Keyboard Layout for X11
------------------------------------

## Background

Emacs users often report problems caused by strain on the pinky finger
that's used to press the `Control` key. The standard answer to that is
to map `Caps Lock` to `Control`. I believe that there is a
[better](http://ep.yimg.com/ca/I/paulgraham_2202_12419224)
[way](http://www.inventinginteractive.com/2010/01/25/symbolics-keyboard/).

Note the placement of modifiers: `Control`, `Meta`, `Super`, `Hyper`
on both sides of `Space` in this order, with `Control` being the
closest to it. Touch typists especially find having two of each key
absolutely essential and the symmetric placement appeals to me.

Also note the `Rubout` key, next to `A` where `Caps Lock` resides on
modern keyboards. `Rubout` is like `Backspace` and is better to have
on the home row than the most useless and annoying key in history.

Under X11, the above are the modifications I make to the default
layout. I keep the original Backspace key too as Backspace, but it
could be `Caps Lock` as well: I don't use it either way. If you have a
narrow `Space` key, you can place your thumbs on the two `Control`
keys while the fingers rest on `asdf` and `jkl`. Always press
modifiers with the alternate hand. `C-a` is right thumb + left pinky,
`C-M-p` is left-thumb + left-ring + right-pinky. For `C-M-P`, add the
left pinky for `Shift`.

Another thing I find tremendously useful is getting used to `C-n`,
`C-p`, `C-b`, `C-f` instead of reaching for the arrow keys as often as
a vi user hits `Escape`.

## How to use it

Like this:

    cd <this-dir>
    xkbcomp -Ixkb/ xkb/keymap/us_lisp $DISPLAY

The xkb is designed for a pc105 (with one Win key) notebook keyboard.
Clearly, for keyboards with different phyiscal layouts, it needs
tweaking.

Oh, switching to `us_lisp` above also swpas `[]` and `()`. Remove
`+lisp(swap_paren_bracket)` from the keymap file if that bit puts you
over the edge.

## About the right meta modifier

On Lenovo keyboards, the `PrtSc` button is often found between `AltGr`
and `Ctrl`, on the right of the space bar (where other keyboards may
have the `Menu` button). This is where the right `Meta` modifier
(`Meta_R` in xkb) should be, so we map both `MENU` and `PRSC` to
`Meta_R`.

    partial modifier_keys
    xkb_symbols "lisp_machine_modifiers" {
        key <LCTL> { [ Super_L, Super_L ] };
        key <RCTL> { [ Super_R, Super_R ] };
        key <LALT> { [ Control_L, Control_L ] };
        key <RALT> { [ Control_R, Control_R ] };
        key <LWIN> { [ Meta_L, Meta_L ] };
        key <MENU> { [ Meta_R, Meta_R ] };
        # On the Lenovo usb Thinkpad keyboard, PRSC is where MENU usually is.
        key <PRSC> { [ Meta_R, Meta_R ] };
        modifier_map Control { <RALT>, <LALT> };
        modifier_map Mod1 { <LWIN>, <MENU> };
        modifier_map Mod4 { <LCTL>, <RCTL> };
    };

However, when `PrtSc` is `Meta_R`, the modifiers on the right side,
e.g. in `C-M-a`, may not work sometimes. This is due to the conflict
with the [Magic SysRq key][magic-sysrq]. I found two ways to make it
work: make sure to press the `PrtSc` key _after_ pressing the `Alt`
key (mapped to `Control_R`), or disable the Magic SysRq key.

  [magic-sysrq]: https://en.wikipedia.org/wiki/Magic_SysRq_key
