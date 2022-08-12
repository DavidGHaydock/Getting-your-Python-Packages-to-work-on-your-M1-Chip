# Getting-your-Python-Packages-to-work-on-your-M1-Chip
I have had a lot of issues using Python packages that have dependencies that the M1 chip doesn't support. 
I wanted to use Python 2, but conda doesn't have a path to it with the M1 installation.
Many packages also use C to install them, which the M1 chip doesn't seem to like either.

This is a workaround which works for me. It essentially has the M1 chip act like an Intel chip - Python doesn't seem to notice. 
*Note you will have to reinstall packages like brew, etc.*

First, I now run everything out of Rosetta. Rosetta, as far as I understand it, is an emulator of the Intel chip.

In the Docker with the terminal open, right click on the Terminal thumbnail, and go to Options > Show in Finder.

Right click on the Terminal, and copy it. 

Rename the copy to "Rosetta". 

Right click on your Terminal named, Rosetta, and select "Get Info", then tick the box for "Open using Rosetta".

Close Rosetta and restart it.

At the bar at the top of the screen go to: Terminal > Preferences...

Click on the "Profiles" tab, then the sub-tab "Shell".

Tick the "Run command" option and change where it says "zsh" to:

```
arch -x86_64 zsh
```

This makes it so that whenever you open the Rosetta Terminal, and anything that you run out of this terminal, will run like it is operating out of an Intel Chip system.

You will now have to reinstall any of the packages that you use for installation. If you use Homebrew, uninstall and reinstall it in this Rosetta terminal. The Homebrew that gets installed should then be in the /usr/local directory like it would be in an Intel system, instead of the /opt folder like it is in M1.

Once this is done however, any of the packages you install with brew will now install as if you were using the Intel chip.

I would recommend installing miniconda3 for Python environments, and choosing the x86_64 Mac installer:
https://docs.conda.io/en/latest/miniconda.html

Using that in the Rosetta terminal works fine, and doing so allows you to create Python 2.7 environments in the M1 Mac no problem!

Installation of anything using pip in any Python environment using this method doesn't cause M1 chip compatibility errors.

If there any issues with this approach let me know. 
I thought I'd put this out there for anyone struggling with the same issues because I am yet to find anything else that has a solid solution. 
Hopefully development will catch up to M1 soon so that this work around isn't necessary.
But until then, enjoy!
