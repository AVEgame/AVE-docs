Making Your Own AVE Game
========================

Before making your own game, download the latest version of AVE:

- [Latest Python build (Linux/Mac)](https://github.com/AVEgame/AVE/releases/download/v1.3/AVE1.3-python.zip).
- [Build from source](/docs/build.md)

To make your own game for AVE, create a file with the extension `.ave` in the `games` folder.
Once your game has been created in the `games` folder, it should appear on the list of games when you run
`run.py`. To run `run.py` open terminal, use `cd` to navigate to the AVE folder, then type `python run.py` or `./run.py`.

Before writing a game, you may find it very helpful to enable syntax highlighting.
Currently, we have implemented syntax highlighting for the text editor nano.
You can find more details about syntax highlighting, and how to enable it [here](/docs/syntax_highlighting.md).

Game Description
----------------
At the top of your `.ave` file, you should give your game a name, description and author(s). This is done as follows:

    == Name ==
    -- Description --
    ** Author(s) **

You may also prevent a game from appearing in the menu on the main screen by adding:

    ~~ off ~~

Rooms
-----
Rooms are started with `#`. There must be a space following this and then the unique ID of the room.
The game will begin in the room with id `start`. 

Text that will appear describing the room for the player should be place on the following lines.

Options for the user should follow the format:

    Description of option => room_id

Where `room_id` is the ID of the room that the player will be sent to.

For example, you could make the following two rooms:

    # start
    You are bored.
    Watch Star Trek => trek
    
    # trek
    You are watching Star Trek.
    Stop watching Star Trek => start

This example will start with you being bored. You will be presented with one option: watching Star Trek. Once you click this option,
you will be sent to the room with ID `trek`, where you have one option: to turn off Star Trek. Doing this sends you back to this first room.

Items
-----
Items can be added to a user's inventory with the `+` symbol at the end of a line.
This can follow either a description line (in which case the item will be added as soon as the user enters the room) or to an option line,
in which case the item will be added before entering the next room. For example:

    Here is a bucket. + bucket

will add a bucket to the players inventory. You can also remove items from a player's inventory with `~`:

    Screw you and your bucket. It's mine. ~ bucket

Options and lines of dialog can be conditionally displayed based upon items in the players inventory. For example:

    Hello there ? bucket

will only be displayed if the user already has the bucket in their inventory. Whereas:

    Goodbye ?! bucket

will only be displayed if the player does not have a bucket in their dictionary.

The `+`, `?`, and `?!` symbols must have leading and trailing whitespace in order to function, so it is possible to have questions in your script.

Items can be described in your game file using the `%` key. Similar to the `#` key for rooms, there must be a space following the key and then the item ID.
For example:

    % bucket
    Empty Bucket

Will display the bucket in the user's inventory as "Empty Bucket". The `?` and `?!` can be used for items as well.

    % bucket
    Empty Bucket !? water
    Full Bucket ? water

These lines will change the display name of an item depending on the presence of water in the player's inventory.
Only the first 18 characters will be displayed in the player's inventory.
By default, any item without a name set will not be shown in the inventory. 

If you need to check whether the player has an empty bucket, you will need to check both item IDs:

    You need water in the bucket. ? bucket ?! water

We are currently working on implementing OR. It should be complete very soon. It will use the following syntax:
    You need bucket or water. ? (bucket water)
    You need bucket or not water. ? (bucket !water)

Game Over
---------
Eventually you'll want the game to end.
You can do this by sending the player to the special `__GAMEOVER__` room, which offers the player the chance to play again or choose another game.
You should not do this immediately on failure, but rather send the player to a room with a some kind of game over text, for example:

    # headbucket
    You accidentally put the bucket on your head and fall down the stairs. You die.
    Continue => __GAMEOVER__

Alternatively, you can send the player to the `__WINNER__` room, which has the same effect as the game over room,
but the text says they have won the game.

Have fun writing amazing games.
