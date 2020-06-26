# compaudit-fixer

When the compaudit command prints warnings, then fix them.

Usage:

    compaudit | compaudit-fixer

Examples:

    $ compaudit
    There are insecure directories and files:
    /usr/local/share/zsh/foo
    /usr/local/share/zsh/goo/hoo

    $ compaudit | compaudit-fixer
    There are insecure directories and files:
    + sudo chown user:group /usr/local/share/zsh/foo
    + sudo chmod 750 /usr/local/share/zsh/foo
    + sudo chown user:group /usr/local/share/zsh/goo/hoo
    + sudo chmod 750 /usr/local/share/zsh/goo/hoo


### Implementation

This script sets the user and group:

* The user is the current system real user

* The group is the first match of these: root, wheel, admin.

This script sets the permissions to 750.
