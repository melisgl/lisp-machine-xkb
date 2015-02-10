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
`C-M-p` is left-thumb + left-ring + right pinky. For `C-M-P`, add left
pinky for `Shift`.

Another thing I find tremendously useful is getting used to `C-n`,
`C-p`, `C-b`, `C-f` instead of reaching for the arrow keys as often as
a VI user hits `Escape`.

## How to use it

Like this:

    cd <this-dir>
    xkbcomp -Ixkb/ xkb/keymap/us_lisp $DISPLAY

The xkb is designed for a pc105 (with one Win key) notebook keyboard.
Clearly, for keyboards with different phyiscal layouts it needs
tweaking.

Oh, switching to `us_lisp` above also swpas `[]` and `()`. Remove
`+lisp(swap_paren_bracket)` from the keymap file if that bit puts you
over the edge.
