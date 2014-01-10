gnome-terminal-profile-switcher
===============================

Gnome Terminal Profile Switcher

This project allows you to change the profile of the terminal you are currently using from a script for
gnome-terminal users. An example "safe_ssh" script is provided to demonstrate a clear use case.

It should be noted that the method to make this work is a hack.



To use, you will first need to create the profiles you wish to swap between within gnome terminal.
Between creating each profile, you can run "gconftool-2 --get /apps/gnome-terminal/global/profile_list"
in order to see the internal names for the profiles stored by gnome terminal - these are the profile
names that are used by the provided script.

You can then create a list of your logical names for profiles and their internal names somewhere convenient
for your own reference.

e.g.

<logical>  <gnome internal>
default    Default
database   Profile0
production Profile1
staging    Profile2


Now you have a list of profiles you can swap between, you can create a gnome-terminal by running the "term"
script with no arguments. This will create a gnome-terminal with a new, temporary profile, and inject two
environment variables: __TERM_PROF and __PROF_CHANGE. These allow you to change the profile of the terminal
by running:

"$__PROF_CHANGE" --change "$__TERM_PROF" <profile to change to>

The term script can be placed in your ~/bin, and you can bind your terminal shortcut(s) to run this script.
