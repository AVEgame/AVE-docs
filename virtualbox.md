Running the VirtualBox Image of AVE
===================================
For users running Windows, or other system without curses, we provide a VirtualBox image of an Ubuntu machine that runs AVE.
You can run this on your computer by installing 
[Oracle VM VirtualBox](https://www.virtualbox.org/wiki/Downloads).

Once you have downloaded and installed 
[Oracle VM VirtualBox](https://www.virtualbox.org/wiki/Downloads), download the [image of AVE](https://github.com/AVEgame/AVE/releases/download/v1.3/AVE1.3-VirtualMachine.ova).
You can then open this in VirtualBox by clicking File -> Import Appliance....

Sharing the `games` Folder
--------------------------
In order to play your own games in the VirtualBox image, you must create a folder that you share with the image.
To do this right click on the AVE machine in the VirtualBox Manager window, and click Settings... then pick Shared Folders on the
panel on the left. Add a shared folder by clicking on the folder with a plus on the right hand side. You will be asked for a Folder Path and
a Folder Name. For the Folder Path choose a directory on your computer in which you would like to save your `.ave` files.
For the Folder Name, type `games`.

Now, start the virtual machine and you can play your own AVE games.

If you ever need it, the username on the image is `ave` and the password is `avegame.co.uk`.
