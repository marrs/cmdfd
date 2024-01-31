# CMDFD: Fuzzy find commands by their description

No longer do you have to remember how to spell `zathura` or `sxiv`.
Search for *pdf reader* or *image viewer* instead.

## Dependencies ##

This script uses the following commands:
- `fzf` for the search interface
- `apropos` to source the default command list
- `vim` to format the default command list

## Usage ##

- `cmdfd [arguments]`
- `cmdfd --update`
- `cmdfd --help`

`cmdfd` will allow you to fuzzy search all of the commands installed to your
`$PATH` by description using `fzf`.  The selected command will then be run
in your terminal.

For performance reasons, the command list is generated and saved to
`$HOME/.local/share/cmdfd/apropos.list`. Subsequent calls will use
this list directly.  To update the list, either delete it, or run
`cmdfd --update`.

The special arguments `--update` and `--help`, apply to `cmdfd` itself.
- `--update` updates the list of available commands.
- `--help` presents information about `cmdfd` to the user.

## Configuration ##

`cmdfd` searches the following lists for command information:
- `$HOME/.local/share/cmdfd/apropos.list`
- `$HOME/.local/share/cmdfd/custom.list`
 
`apropos.list` is a list of all the commands available to your shell,
generated internally from `apropos -s 1 ''`.  It can be rebuilt
with `cmdfd --update`.

`custom.list` can be edited by you directly to provide descriptions for any
custom commands (with arguments) you may wish to save.

Each item in the lists is of the format:
`[command [args]] -:- [description]`

For example:
`feh --bg-fill	-:- Set your wallpaper (filled)`
