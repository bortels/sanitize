sanitize
========

A script to sanitize your history files
---------------------------------------

I test from the command line - a lot. And bits of sensitive data (mostly credentials)
tend to creep in, and get immortalized in my history files, waiting for some savvy
script kiddie to make my life difficult. Maybe this will help.

Called with no parameters, it reads "~/.sanitize" for a list of hashes,
then iterates thru files in the home directory matching ".*_history", checking
#or any character sequences that match the hash list, replacing any found with
some underscores.

Called with an argument, it adds the hash of that argument to the .sanitize file.
By saving a hash rather than the actual credential, we can compare text to see if
it matches without having to save the actual credential for someone to find.

When calling this with an argument, be sure to prepend a space or run it again without
an argument afterwards to remove your plaintext password.

Note you may need to login/logout to make your shell reflect these changes.

This was written on OS X under Oh My Zsh! - I expect it to work other places, but YMMV.
Do be careful. 

In zsh, I use this by adding a "trap 'sanitize' EXIT" to my .zshrc, so it is run automatically
when I exit the shell. Seems to work. 

Why perl? because perl is everywhere, and so this should run without prereqs anywhere.
except maybe windows. Dunno.
