Website Reference
=================
The different versions of AVE all use the game library on this website.
This page contains details of how to access games in this library.

gamelist.json
-------------
`http://www.avegame.co.uk/gamelist.json` contains a list of all available AVE games.
This includes both the default games and the user contributed games.
The games in this json will appear in the following format:

```
    %%string id%%:[
               "title":%%string title%%,
               "author":%%string author%%,
               "desc":%%string desc%%,
               "active":%%bool active%%,
               "user":%%bool user%%
              ]
```

%%id%% will end in `.ave` and gives the location of the `.ave` game file (`http://www.avegame.co.uk/download/%%id%%`).
For the `.json` game file, replace the `.ave` with `.json`. For all user games, %%id%% starts with `user/`.

%%title%%, %%author%% and %%desc%% give the title, author(s) and description of the game, taken from the `.ave` file.
%%active%% tells whether or not the game is active. %%user%% tells whether or not the game is a user game.

download/%%filename%%.ave and download/user/%%filename%%.ave
--------------------------------------------------------
`http://www.avegame.co.uk/download/%%filename%%.ave` and `http://www.avegame.co.uk/download/user/%%filename%%.ave` will give you the `.ave` 
files of the game.

Please note: the %%id%% from `gamelist.json` will include `user/` (if it's a user game) and `.ave`.

download/%%filename%%.items and download/user/%%filename%%.items
--------------------------------------------------------
`http://www.avegame.co.uk/download/%%filename%%.items` and `http://www.avegame.co.uk/download/user/%%filename%%.item` will give you just the
items from the `.ave` file of the game.

Please note: the %%id%% from `gamelist.json` will include `user/` (if it's a user game) and `.ave`. This `.ave` should be replaced with `.items`
if the items file is desired.


download/%%filename%%.json and download/user/%%filename%%.json
----------------------------------------------------------
`http://www.avegame.co.uk/download/%%filename%%.json` and
`http://www.avegame.co.uk/download/user/%%filename%%.json`
will give you the `.json` files of the game.

Please note: the %%id%% from `gamelist.json` will include `user/` (if it's a user game) and `.ave`. This `.ave` should be replaced with `.json`
if the json file is desired.

The json file will have the following format:

```
    {
     "rooms":%%dict rooms%%,
     "items":%%dict items%%,
     "loaded":%%bool loaded%%
    }
```

%%rooms%% and %%items%% will contain the game data. %%loaded%% tells you whether the game has loaded properly. If %%loaded%% is false, it is most
likely that the game does not exist.

The items in %%rooms%% will have the following format:

```
    %%string id%%:[
                 %%string id%%,
                 %%list info%%,
                 %%list options%%
                ]
```

%%id%% is the ID of the room.

%%info%% will contain items of the format `{"text":%%string text%%,"needs":%%list needs%%,"unneeds":%%list unneeds%%,"adds":%%list adds%%,"rems":%%list rems%%}`.
%%text%% is the text that will be shown if %%needs%% and %%unneeds%% are satisfied. If this text is shown, then %%adds%% and %%rems%% will be added and removed.

%%options%% will contain items of the format `{"id":%%option_id%%,"option":%%string text%%,"needs":%%list needs%%,"unneeds":%%list unneeds%%,"adds":%%list adds%%,"rems":%%list rems%%}`.
These options will be offered to the player if %%needs%% and %%unneeds%% are satisfied.
If the option is chosen, %%adds%% and %%rems%% will be added and removed, then the player will be sent to the room with ID %%option_id%%.

The items in %%items%% will have the following format:

```
    %%string id%%:[
                 %%list names%%,
                 %%bool hidden%%,
                 %%bool number%%,
                 %%int start_value_for_number%%
                ]
```

%%names%% will contain items of the format `{"name":%%string name%%,"needs":%%list needs%%,"unneeds":%%list unneeds%%,"adds":%%list adds%%,"rems":%%list rems%%}`.
%%name%% will appear in the inventory if the item is held and %%needs%% and %%unneeds%% are satisfied.
%%adds%% and %%rems%% are probably not implemented (as it's not at all clear what they should do).

%%hidden%% should always be `false`. It was previously set to `true` when the deprecated `__HIDDEN__` was added to an item.
