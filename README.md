If you have lots of keybindings set in your .emacs file, it can be hard to know which ones you haven't set yet -- and which may now be overriding some new default in a new Emacs version.  This module aims to solve that problem.

Bind keys as follows in your .emacs:

    (require 'bind-key)

    (bind-key "C-c x" 'my-ctrl-c-x-command)

If you want the keybinding to override all minor modes that may also bind the same key, use the `bind-key*` form:

    (bind-key* "<C-return>" 'other-window)

If you want to rebind a key only for a particular mode, use:

    (bind-key "C-c x" 'my-ctrl-c-x-command some-other-mode-map)

To unbind a key within a keymap (for example, to stop your favorite major mode from changing a binding that you don't want to override everywhere), use `unbind-key`:

    (unbind-key "C-c x" some-other-mode-map)

After Emacs loads, you can see a summary of all your personal keybindings currently in effect with this command:

    M-x describe-personal-keybindings

It will tell you if you've overriden a default keybinding, and what that default was.  Also, it will tell you if the key was rebound after your binding it with `bind-key`, and what it was rebound it to.
