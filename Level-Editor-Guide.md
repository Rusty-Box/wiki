# How to use the Level Editor

> If you are looking for how to **package your levels and worlds as Add-Ons** so you can submit them
  to our Add-On manager, go [here](https://github.com/SuperTux/supertux/wiki/Add-ons#packaging-addons)!

Beginning Steps
===============

Upon opening the level editor you have the option to open an existing world/levelset or create one of your own.
For this guide we will start fresh and create a new one.

Select `Create World` and enter a name and description for your new world. The description is optional so if you
are unsure what to write, just skip it and select `OK`.

![](images/editor/create_world.png "Creating a new world")

Now you can begin to create your first level (or worldmap).

## Contents

### For making Levels
1. [Setting up your Level](#Setting-Up-Your-Level)
   * [General Tools](#General-Tools---Tile-Mode)
3. [Tiles and Tilemaps](#Tiles-And-Tilemaps)
   * [Tilemaps](#Tilemaps)
4. [Objects and Badguys](#Objects-And-Badguys)
   * [Using Doors](#Using-Doors)
   * [Using Info Blocks](#Using-Info-Blocks)
5. [Adding a Goal](#Adding-a-Goal)
6. [Secret Areas](#Secret-Areas)
7. [Using Pathnodes](#Using-Pathnodes)
8. [Ambient Light](#Ambient-Light)
9. [Scripting](#Scripting)

### For making Worldmaps
1. [Setting up your Worldmap](#Setting-Up-Your-Worldmap)
2. [Using Teleporter](#Using-Teleporter)
3. [Using Sprite Change](#Using-Sprite-Change)

---

Setting Up Your Level
=====================

You are now presented with a snowy background and a lot of empty space.

On the right you see the Tile Select, Object Select and your general tools. On the bottom you will find several
means to edit the level sector.

General Tools - Tile Mode
-------------------------

In Tile Mode you cannot interact with objects at all! It is active as long as your are in one of the tile categories.

- ![](https://github.com/SuperTux/supertux/blob/master/data/images/engine/editor/select-mode0.png?raw=true)
  The **Red-Selection** is the most basic tool. It allows you to place single tiles.
- ![](https://github.com/SuperTux/supertux/blob/master/data/images/engine/editor/select-mode1.png?raw=true)
  The **Green-Selection** allows placing multiple instaces of a tile or group of tiles by holding the
  left mouse button.
- ![](https://github.com/SuperTux/supertux/blob/master/data/images/engine/editor/select-mode2.png?raw=true)
  The **Fill-Bucket** lets you fill an area with the selected tile.
- ![](https://github.com/SuperTux/supertux/blob/master/data/images/engine/editor/rubber.png?raw=true)
  The **Eraser** simply removes tiles from your level.
  
To access the **Green-Selection** or **Fill-Bucket** tool you have to click on the **Red-Selection** tool to swap between the three!

General Tools - Object Mode
---------------------------

In Object Mode you cannot interact with tiles at all! It is active as long as your are in one of the object categories.
To configure an object's properties simply right-click on the object you wish to configure.

- ![](https://github.com/SuperTux/supertux/blob/master/data/images/engine/editor/arrow.png?raw=true)
  The **Selection** tool is used to select objects from your level.
- ![](https://github.com/SuperTux/supertux/blob/master/data/images/engine/editor/rubber.png?raw=true)
  The **Eraser** simply removes objects from your level.
- ![](https://github.com/SuperTux/supertux/blob/master/data/images/engine/editor/move-mode1.png?raw=true)
  The **Duplicator** can be used to duplicate an object on the spot.

To access the **Duplicator** tool you have to click on ![](https://github.com/SuperTux/supertux/blob/master/data/images/engine/editor/move-mode0.png?raw=true)
and vice versa.

- ![](https://github.com/SuperTux/supertux/blob/master/data/images/engine/editor/path_node.png?raw=true)
  The **Pathnode** tool allows drawing pathnodes for moving objects, see [Using Pathnodes](#Using-Pathnodes).

Unlike the other tools you only find the **Pathnode** tool under `Objects` → `Environment`.


Tiles And Tilemaps
==================

Let's make a basic level. First, click on `Tiles` in the top-right and select a category of your choosing.

Select the tile you would like to use by clicking on it. You can select multiple tiles at once by holding the
Left-mouse button and dragging your mouse over the tiles you want to select. Your selection is now displayed
besides the cursor, moving across the grid. By left-clicking you can place them now as many times as you want.

**Note: By right-clicking on a tile inside your level, you can copy it. This can save you time if you don't want to
frequently switch back and forth between categories.**

Tilemaps
--------

To have Tux be able to stand on your tiles you need to place them on a solid tilemap.

A tilemap is where all tiles of a level are drawn. They help organizing your tiles and allow for using multiple layers.
You can add a tilemap through the `Sector` category in the Objects menu. The default solid tilemap is marked `0` in
the bottom bar. You can edit pre-existing tilemaps by right-clicking on their icon.

![](images/editor/tilemap_layers.gif "The three default tilemaps for levels")

Every newly created level comes with three tilemaps by default. One for background elements, one for foreground elements
and one for solid ground. Their marked number is defined by their Z-postion. If the Z-position is set to 50 or below, the
tilemap is behind Tux; otherwise it is in front of Tux. The default background tilemap is marked `-100` and the default
foreground tilemap is marked `100`.

In the tilemap settings you can change their size, solidity, Z-position, as well as the color of the tiles themselves using RGBA
values (Red, Green, Blue, Alpha).

You can also use tilemaps to darken or brighten tiles. Add a new unsolid tile map and set the alpha value to a number
between 0 (0%) and 1 (100%). Under the `Unisolid + Lightmap` category of the Tiles menu you find tiles best suited for this.

If you enable `Following path` and reselect the tilemap, you will see a small gray circle at the top-left corner of the tilemap.
You can now click and move the tilemap around as well as have it move. See [Pathnodes](#Using-Pathnodes) for more info!


Adding Objects And Badguys
==========================

Now that you have build your level, let's take a look at how to place objects, such as enemies, moving platforms,
ladders, script triggers, and more. While in **Object Mode** you cannot interact with tiles!

First, click on `Objects` in the top-right and select a category. Upon placing an object you can edit some of their
properties by right-clicking on the object.

**Note: You cannot interact with objects while in Tiles Mode!**

Using Doors
-----------

For a door to work properly you must first define a destination. This is done by adding another spawnpoint and naming it.
Now everything left to do is enter the names of the sector and the spawnpoint you want to Tux to go when using the door,
et voilà!

![](images/editor/how_to_door.png "Define destination for doors")

Using Info Blocks
-----------------

Info Blocks can be given messages, such as explanations. Right-click the info block to add a message. The first character
of a paragraph can be used for formatting. This character will not be displayed in the actual message:

- A hash `#` is usually used for normal text.
- A hyphen-minus `-` is used for headlines.
- An exclamation mark `!` alongside an image path `images/...` displays the image in the text.
- An asterisk `*` displays the text blue and centered.
- <kbd>Space</kbd> makes the text small.

---

Adding A Goal
=============

Every level requires a goal to be finishable!

For an area to be defined as a goal we will make use of the **Sequence Trigger** which is found in the `Environment`
category of the Objects menu. Place one around something like a goalpost and make sure its sequence is set to `end sequence`.

![](images/editor/making_a_goal.png "Making a goal with Sequence Triggers")

The sequence trigger on the right is used to prevent Tux from walking further right and out of the igloo. For that simply
place another sequence trigger and set its sequence to `stop Tux`.


Secret Areas
============

The usage of secret areas is a good way to encourage exploration in your level.

There are many ways to set up secret areas in SuperTux. The most common one is a place hidden behind a wall
which is revealed once the player enters it. For that you will need to add a new tilemap and give it a name!
Next you can find the secret area trigger under `Environment` in the Object menu represented by a green
square near the bottom.

Once you placed your secret area trigger, make sure it covers the area you wish to turn into a secret area.
Last but not least, right-click the secret area trigger and enter the name of your tilemap that will cover
the secret area to insure that it will fade away when found!

![](images/editor/secret_area.png "Making a secret area covered by a tilemap")


Using Pathnodes
===============

Pathnodes are used to form a path for platforms, coins, tilemaps etc. to move on.

To do this, select the object and click with the **Pathnode tool** on the small gray circle on its top-left. If you now
click anywhere else in your level, you will draw a new path node between it and the last node you selected. For coins and
tilemaps, make sure you have `Following path` enabled!

You can find the tool under `Environment` in the Objects menu as a red arrow pointing to the right.

![](images/editor/drawing_pathnodes.png "Drawing Pathnodes for a moving platform")

After setting up your pathnodes you can now edit each node’s properties by right-clicking each individual node.

![](images/editor/pathnode_properties.png "Properties of a pathnode")


Ambient Light
=============

To use things like lanterns, magic blocks or anything else that can emit light and have it shown, you must darken the
sector beforehand. Right-click the lightbulb icon next to your tilemaps and define the sector's ambient light using **RGBA**.
Give each value a number between 0 (0%) and 1 (100%).

![](images/editor/ambient_light.png "Defining RGBA values of the ambient light object")


Scripting
=========

Scripting allows for much more dynamic elements to be used in level creation. Scripts are written in **Squirrel** and
can be triggered in many different ways:

- A common one is the **Script trigger** object. It marks the area in which the script will be executed with a pink
  square and can be resized as desired. The script gets triggered when Tux enters this area.
- If you wish to execute a script immediately after entering a sector you can do that with the **Initialization script**.
  You will find it in the settings of your sector. Mind you, the script will also be executed every time you restart from
  a checkpoint in that sector!
- Badguys may also serve as a way to use scripts. Each badguy can be given a **Death script** that is executed upon
  the enemy's defeat. This method is commonly used for Bosses, for example `sector.Tux.trigger_sequence("fireworks");`
  for the Yeti Boss in Icy Island.
- Other prominent methods for scripts are buttons/switches, picking up powerups or running into Will ’O’ Wisp.

**For a list of commands that can be used in scripts, take a look at the [scripting reference](https://github.com/SuperTux/supertux/wiki/Scripting_reference).**

---

Setting Up Your Worldmap
========================

Back in the level menu of your world you can click on `Create Worldmap` to start working on a worldmap.

You are now presented with a tilemap that is filled with dark blue tiles, representing the ocean. We recommend you to
change the tileset in your worldmap settings from `worldmap.strf` to `ice_world.strf` as it grants much more diverse
and fleshed-out tiles.

![](images/editor/change_tileset_wm.png "Changing the tileset of a worldmap")

Worldmap creation works similar to level making. The biggest difference stems from the objects which there is only
a small amount. Instead of Badguys, Moving Platforms and Blocks you only have Leveldots, Teleports, Special Tiles
and Sprite Changer.

- ![](https://github.com/SuperTux/supertux/blob/master/data/images/worldmap/common/leveldot_red.png?raw=true)
  A **leveldot** allows the player to enter a predefined level from the worldmap.
- ![](https://github.com/SuperTux/supertux/blob/master/data/images/worldmap/common/teleporterdot_1.png?raw=true)
  A **teleporter** moves Tux from one place to another in an instant.
- ![](https://github.com/SuperTux/supertux/blob/master/data/images/worldmap/common/messagedot.png?raw=true)
  A **special tile** can be used to initiate scripts or show messages.
- ![](https://github.com/SuperTux/supertux/blob/master/data/images/engine/editor/spritechange.png?raw=true) 
  A **sprite change** lets you change Tux's appearence on the worldmap when touched.


Using Teleporter
================

The teleporter is set up similarly to a door in a level. First, you need an additional spawnpoint for where you want Tux to
teleport to and name it. Then you enter the name of the spawnpoint in the teleporter's settings. You can also select a target
worldmap, if you want it to teleport Tux to a completely different worldmap.

Enabling `Automatic` will cause it to teleport Tux instantaneous upon touching the teleporter.


Using Sprite Change
===================

For a simple sprite change select the sprite you want Tux to change into and make sure `Change on touch` is enabled.

To have something like a boat present on your worldmap you must also enable `Initial stay action` and name the **stay action**
and **stay group**. For the boat, simply name both of them `boat`.

![](images/editor/define_boat_wm.png "Setting up a boat for a worldmap")

Note: Do not forget to add another sprite changer that does change the sprite back to Tux if the sprite change is only meant
to be temporary!

---

**For more information on how to design levels and aspects such as badguy/objects behavior etc. we recommend the following:**

-   [Level Design](https://github.com/SuperTux/supertux/wiki/Level-Design)
-   [Badguys](https://github.com/SuperTux/supertux/wiki/Characters#Badguys)
-   [Objects](https://github.com/SuperTux/supertux/wiki/Objects)

See also
--------

-   [Level Format](https://github.com/SuperTux/supertux/wiki/Level-Format)
-   [Sharing Levels](https://github.com/SuperTux/supertux/wiki/Level-Editor#Sharing-Levels)
