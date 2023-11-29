
Skin Mod Helper Guide
======================
This guide will walk you through making your skinmod compatible with Skin Mod Helper Plus.

A brief introduction to config files
------------------------------------

Config files give SMH+ information about your skinmod.
You need to create a file named "SkinModHelperConfig.yaml" in your mod root (next to your everest.yaml).


Here is a skeleton of a SkinModHelperConfig.yaml file.
Each of the fields will be explained below.

```yaml
- SkinName: [A SkinName that is required]

  # ---Player skin---
  Player_List: [true/false]
  Silhouette_List: [true/false]
  
  Character_ID: [new Player ID]
  hashSeed: [SkinName]
  
  OtherSprite_Path: [a path]
  
  # ---General skin---
  General_List: [true/false]
  OtherSprite_ExPath: [a path]
```
<br>



SkinName
-----------------------------------
This is the name of your skin that will appear in Mod Options. Remember to clean the name using language files.
```yaml
- SkinName: "Example Skin"    # required
```
<br>



Character_ID
---------------------------

A player skin needs a unique character ID.

```yaml
  Character_ID: "MySkin"
```

This is the ID that you modify in the sprites.xml instead of the normal  `<player>`

```xml
  <!-- sprites.xml -->

<?xml version="1.0" encoding="utf-8" ?>
<Sprites>
  <MySkin copy="player" path="characters/MySkin1/" />
</Sprites>
```
<br>



Conditional Player Sprites
-----------------------------------
You can add additional Character_IDs for your skin that change your skin when specific conditions are met.<br>
If a texture is missing from a conditional player skin, it is filled in from the default player skin.


* "[SkinName] + _NB" 
   * condition: When the player is in no_backpack state
<br><br>
* "[SkinName] + _lantern"
   * If you want reskin some Player ID from JungleHelper, then you can use this special jump
   * condition: Player holds the lantern from JungleHelper
<br><br>
* "[SkinName] + _lantern_NB"
   * conditions: Player holds the lantern from JungleHelper and is in no_backpack state
<br><br>


```yaml
# SkinModHelperConfig.yaml

# ---Default Player skin---
- SkinName: "Example Skin"
  Player_List: true
  Silhouette_List: false
  Character_ID: "MySkin"


# ---Player skin without a backpack---
- SkinName: "Example Skin_NB"
  Character_ID: MySkin_No_Backpack


# ---Player skin holding a lantern---
- SkinName: "Example Skin_lantern"
  Character_ID: MySkin_Lantern
```
```xml
  <!-- sprites.xml -->

<?xml version="1.0" encoding="utf-8" ?>
<Sprites>
  <MySkin copy="player" path="characters/MySkin1/" />
  <MySkin_No_Backpack copy="player_no_backpack" path="characters/MySkin1_NB/" />
  <MySkin_Lantern copy="player" path="characters/MySkin1_Lantern/" />
</Sprites>
```

<br>



OtherSprite / Some thing about skin's Xml
-----------------------------------
Skin will need you to have an Xml file, 
Now let we first set root directory for those Xml, or called them is skin's xml.
```yaml
# The starting point of below path: "Graphics/"
  OtherSprite_Path: [Root directory path]     # for paleyr skin
  OtherSprite_ExPath: [Root directory path]     # for general skin
```
For information about those Xml files, we quote some [everest's wiki](https://github.com/EverestAPI/Resources/wiki/Reskinning-Entities#reskinning-entities-through-spritesxml).
After viewing, we need to do those:
* Remove the some content, or called ID in the skin's Xml that you not have or not want reskin.
  * ! SkinModHelper has a menu to listing all of them, so this very important.
* Then if your skin type is "Player Skin":
  * Create another file calls "Sprites.xml" in "Graphics/" directory
  * Move some PlayerID in the skin's xml to that another xml.
  * Renaming that PlayerID to [Character_ID] that comes from you setted in this config
    * ! If you do this wrong, the game will crash when you enter the map
  * If you have some questions about playerID is what, so [check here](https://github.com/AAA1459/SkinModHelper/wiki/Textures-list-of-Various-Type#maddy-or-baddy-related)
*  Skin's xml not only include "Sprites.xml", it also can include "Portraits.xml"
   * The specific operation is as above.
   
now you have finished them, Let's check out the other parts.

<br>



Make your skin appear in Mod Options
-----------------------------------
If your skin type is "Player Skin", Then We need to use some more content to let it get there:
```yaml
  Player_List: true    # Affects the "Player Skin" option
  Silhouette_List: true    # Affects the "Silhouette Skin" option
```
If your skin type is "General Skin", Then when you set "[OtherSprite_ExPath]" after, them will appear in "General Skin" list.
Or use this to prevent it get there:
```yaml
  General_List: false
```
<br>



HashSeed
-----------------------------------

SkinModHelper skins are CelesteNet compatible. The hashSeed is a unique value that is used to identify your skin. If not included, it defaults to "[SkinName]", but can be overwritten if it conflicts with another skinmod.

```yaml
  hashSeed: [any]
```
<br>



Standard example of config file
-----------------------------------
You can download them as examples for making skins: 
* [Touhou-cirno](https://gamebanana.com/mods/316584)
* [OshiroBoss But Badeline](https://gamebanana.com/mods/444994)



More Miscellaneous
---------------------
1. SkinModHelper have some introduce of special textures, and collected various sources of IDs animation.
   [clike here for check](https://github.com/AAA1459/SkinModHelper/wiki/Textures-list-of-Various-Type#special-texture-settingreskin)

2. more complicated things
   * [Setting ColorGrade for skin](/docs/guide//skinconfig/ColorGrade.md)
   * [Setting HairConfig for skin](/docs/guide//skinconfig/HairConfig.md)
   * [Setting some effects for skin](/docs/guide/skinconfig/CharacterConfig.md)



Troubleshooting
-----------------------
If your skin is not be registered (or does not appear in the menu):
* Make sure your configuration file is named correctly and in the right place
* Check your log to see your skin report anything when trying to register
* If the log says nothing, see this section: 
  [let your skin appear in Mod-Options](#let-your-skin-appear-in-mod-options)

If your sprites/portraits are not appearing in-game:
* Make sure your XML is valid. You can compare to the vanilla files or use an [online syntax checker](https://www.xmlvalidation.com/)
* Make sure the "path" fields to your sprites/portraits are correct and the files are in the right place
* Make sure the "start" field references an animation you have reskinned.

If you get missing textures or unexpected vanilla textures:
* Check your log to see what textures are missing -- these messages can point you in the right direction
* Make sure the number of images matches the number of animation "frames"

If some xml-undefined textures are misaligned:
1. In the same folder as that texture, create a .meta.yaml file with the name of that texture
   * If the texture is "madeline.png", So create "madeline.meta.yaml" flie
2. Write that texture information to the .meta.yaml file you create
```yaml
X: [X offset value of texture in game]
Y: [Y offset value of texture in game]
Width: [pixel Width of texture]     # maybe, game need get its center point
Height: [pixel Height of texture]
Premultiplied: [true/false]    # about this i don't know.
```
3. Restart the game to make it work or reload

If you get crashes:
* Check your log to see if it's a missing texture
* Make sure you don't have any "Metadata" sections for missing animations in Sprites.xml
* Contact me!

If you want to find all vanilla textures (png format):
* You can find it here: [Celeste Graphics Dump v1400](https://drive.google.com/file/d/1ITwCI2uJ7YflAG0OwBR4uOUEJBjwTCet/view)

This process can be pretty involved, especially if you are porting over an existing skin mod,
so feel free to [contact me](../../README.md#contact) if you need help, find an issue, or would
like a new feature supported! You can also use a currently supported skin mod as a reference.

