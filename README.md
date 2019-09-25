Window Tiling
https://www.macupdate.com/app/mac/61314/tiles

Open in terminal Context-Menu
https://github.com/qparis/FinderOpenTerminal

Anaconda PATH on fish shell

```
export PATH="/Users/dishendra/anaconda3/bin/:$PATH"
```


###Mac Change Global View Options

Use as Defaults is supposed to carry over to all newly opened Finder windows, but it doesn't change any previously opened windows. If you want to revert all previously opened windows to that view, follow these steps:



Launch the Terminal app (in /Applications/Utilities/), copy & paste this command into the window that pops up, and hit the return key:



sudo find / -name ".DS_Store"  -exec rm {} \;



At the Password: prompt, carefully enter your admin password, since nothing shows up on the screen, and hit the return key. When the default prompt, usually the $ sign, pops up again, quit the Terminal app, restart, and open a Finder window, set it up the way you want, and click on Use as Defaults button. All subsequently opened or created folders should retain that view. 



# Mac OS X: Launch Terminal from keyboard shortcut

https://claudiodangelis.com/osx/2012/09/27/osx-launch-terminal-from-shortcut.html

