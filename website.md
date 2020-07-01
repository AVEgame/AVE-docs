Website Reference
=================
The different versions of AVE all use the game library on this website.
This page contains details of how to access games in this library.

gamelist.json
-------------
`http://www.avegame.co.uk/gamelist.json` contains a list of all available AVE games.
This includes both the default games and the user contributed games.
The games in this json will appear in the following format:
    %%string id%%:[
                 "title":%%string title%%,
                 "author":%%string author%%,
                 "desc":%%string desc%%,
                 "active":%%bool active%%,
                 "user":%%bool user%%
                ]

%%id%% will end in `.ave` and gives the location of the `.ave` game file (`http://www.avegame.co.uk/download/%%id%%`).
For the `.json` game file, replace the `.ave` with `.json`. For all user games, %%id%% starts with `user/`.

%%title%%, %%author%% and %%desc%% give the title, author(s) and description of the game, taken from the `.ave` file.
%%active%% tells whether or not the game is active. %%user%% tells whether or not the game is a user game.

download/%%filename%%.ave and download/user/%%filename%%.ave
--------------------------------------------------------
`http://www.avegame.co.uk/download/%%filename%%.ave` and `http://www.avegame.co.uk/download/user/%%filename%%.ave` will give you the `.ave` 
files of the game.

Please note: the %%id%% from `gamelist.json` will include `user/` (if it's a user game) and `.ave`.
