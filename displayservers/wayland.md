# Wayland

## [Tip] Use Xorg Backend To Run Apps Under Wayland

### Description

A lot of applications still don't work natively on Wayland. For this, you need to run those applications using Xorg backend.

Some apps may never work on Wayland because of this. They may require Xorg backend.

### Solution

Add **GDK_BACKEND=x11** before every command/app you want to run. For example, if you want to run steam using the X11 backend, run:

    GDK_BACKEND=x11 steam

And so on for all the other commands you want.
