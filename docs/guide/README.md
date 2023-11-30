
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
# SkinModHelperConfig.yaml

- SkinName: [name]                    # Required

  # ---Options for player skins---
  Character_ID: [new Player ID]       # Required
  hashSeed: [name]                    # Optional, defaults to Character ID

  Player_List: [true/false]           # Optional, defaults to false
  Silhouette_List: [true/false]       # Optional, defaults to false
  
  OtherSprite_Path: [a path]          # Optional
```
<br>




# Creating a player skin

SkinName
-----------------------------------
This is the name of your skin that will appear in Mod Options. Remember to clean up the name using language files.
```yaml
- SkinName: "Example Skin"    # required
```
<br>



Character ID
---------------------------

Every player skin needs an unique character ID.

```yaml
  Character_ID: "MySkin"
```

This becomes the ID that you modify in the sprites.xml instead of the normal  `<player>`

```xml
  <!-- sprites.xml -->

<?xml version="1.0" encoding="utf-8" ?>

<Sprites>
  <MySkin copy="player" path="characters/AAA1459/MySkin1/" />
</Sprites>
```
<br>



Sprites.xml
-----------------------------------
SMH+ uses xml files to edit sprites. Visit [everest's wiki](https://github.com/EverestAPI/Resources/wiki/Reskinning-Entities#reskinning-entities-through-spritesxml) for a more comprehensive guide on xml files.


Create a sprites.xml file into the `Graphics/` folder. Only use this sprites.xml to edit the custom character IDs that SMH+ provides. See [OtherSprite Path](https://github.com/testuko/SMHPlus-Guide/blob/main/docs/guide/README.md#othersprite-path) for skinning other sprites.

```xml
  <!-- sprites.xml -->

<?xml version="1.0" encoding="utf-8" ?>

<Sprites>
<!-- Sprite ID "MySkin" is defined by the Character_ID -->
  <MySkin copy="player" path="characters/AAA1459/MySkin1/" />
</Sprites>
```
Only include sprites that you want to reskin. This is very important.<br>
The sprites.xml can also include sprites from protraits.xml.<br>
If the sprite ID doesn't match character_ID the game will crash.
<br><br>



Conditional Player Sprites
-----------------------------------
You can add additional Character IDs for your skin that change your skin when specific conditions are met.<br>
If a texture is missing from a conditional player skin, it is filled in from the default player skin.

These are the current conditional player sprites:
* "[SkinName] + _NB" 
   * condition: When the player is in the no_backpack state
<br><br>
* "[SkinName] + _lantern"
   * condition: Player holds the lantern from JungleHelper
<br><br>
* "[SkinName] + _lantern_NB"
   * condition: Player holds the lantern from JungleHelper and is in the no_backpack state
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
  <MySkin copy="player" path="characters/AAA1459/MySkin1/" />
  <MySkin_No_Backpack copy="player_no_backpack" path="characters/AAA1459/MySkin1_NB/" />
  <MySkin_Lantern copy="player" path="characters/AAA1459/MySkin1_Lantern/" />
</Sprites>
```
<br>



OtherSprite Path
---
In order to change other sprites when your skin mod is enabled, you can create a second sprites.xml file that gets applied when the specific skinmod gets loaded. Edit all other sprites here.
This can also be used to reskin custom animations from other helpers. 

The sprite path is relative to the `Graphics/` folder.

```yaml
  OtherSprite_Path: "AAA1459/MySkin1"    # Path to the skin specific sprites.xml
```



Example sprites.xml
```xml
 <!-- Graphics/AAA1459/MySkin1/sprites.xml -->

<?xml version="1.0" encoding="utf-8" ?>

<Sprites>

  <payphone path="cutscenes/payphone/AAA1459/MySkin1/" start="idle">
    <Justify x=".5" y="1" />
    <Loop id="idle" path="phone" delay="0.1" frames="0"/>
    <Anim id="pickUp" path="phone" delay="0.08" frames="1-11"/>
    <!-- shortened -->
  </payphone>


  <!-- HonlyHelper -->
  <HonlyHelper_CatPetter path="characters/HonlyHelper/ThePetter/AAA1459/MySkin1/" start="pet">
    <Loop id="pet" path="player_pet" delay="0.15"/>
  </HonlyHelper_CatPetter>

  <CollabUtils2_sitBench path="CollabUtils2/characters/AAA1459/MySkin1/" start="sit">
    <Justify x="0.5" y="1.0" />
    <Anim id="sit" path="sitBench" delay=".08" frames="0-17"/>
    <Anim id="sitHair" path="sitBenchHair" delay=".08" frames="0*9,1*5,2*4"/>
  </CollabUtils2_sitBench>

</Sprites>
```
<br>



Make your skin appear in Mod Options
-----------------------------------

If you are making a player skin, you have to specify where it shows up in the Mod Options.
```yaml
  Player_List: true    # Makes the skin show up in the player skin list.
  Silhouette_List: true    # Makes the skin show up in the silhouette skin list.
```
<br>



HashSeed
-----------------------------------

SkinModHelper skins are CelesteNet compatible. The hashSeed is a unique value that is used to identify your skin. If not included, it defaults to "[SkinName]", but can be overwritten if it conflicts with another skinmod.

```yaml
  hashSeed: "Example Skin"    # Any unique string, recommended to be your Skin Name
```
<br><br>


# Creating a general skin
General skins are used skin other entities than the player. They only neet 2 parameters. 


```yaml
# SkinModHelperConfig.yaml

- SkinName: [name]                    # Required
  
  # ---Options for general skins---
  General_List: [true/false]          # Choose if the skin shows up in the options menu or not
  OtherSprite_ExPath: [a path]        # Works the same way as OtherSprite_Path
```

General skins work just like [OtherSprite Path](https://github.com/testuko/SMHPlus-Guide/blob/main/docs/guide/README.md#othersprite-path), except they use OtherSprite_ExPath.
<br>
<br>
<br>


# Multiple skins in one mod
You can define multiple skins inside the SkinModHelperConfig.yaml

```yaml
# SkinModHelperConfig.yaml

  # ---First player skin---
- SkinName: "Example Skin 1"
  Player_List: true
  Character_ID: "MySkin_1"

- SkinName: "Example Skin_1_NB"
  Character_ID: "MySkin_1_NB"


  # ---Second player skin---
- SkinName: "Example Skin 2"
  Player_List: true
  Character_ID: "MySkin_2"
  OtherSprite_Path: "AAA1459/MySkin_2"

- SkinName: "Example Skin_2_Lantern"
  Character_ID: "MySkin1_2_Lantern"


  # ---Third player skin---
- SkinName: "Example Silhouette"
  Player_List: false
  Silhouette_List: true
  Character_ID: "MySkin_Silhouette"


  # ---Fourth general skin---
- SkinName: "Example Strawberry Retexture"
  General_List: true
  OtherSprite_ExPath: "AAA1459/berry"
```
<br>



Example skins
-----------------------------------
You can download these skins and use them as reference when making skins: 
* [Touhou-cirno](https://gamebanana.com/mods/316584)
* [OshiroBoss But Badeline](https://gamebanana.com/mods/444994)



More Miscellaneous
---------------------
1. Here is a small collection of animations and textures you can change (not comprehensive). It also lists the custom textures that SMH+ adds.
   [clike here to check](https://github.com/AAA1459/SkinModHelper/wiki/Textures-list-of-Various-Type#special-texture-settingreskin)

2. Slightly more complicated settings
   * [Setting ColorGrade for skin](/docs/guide//skinconfig/ColorGrade.md)
   * [Setting HairConfig for skin](/docs/guide//skinconfig/HairConfig.md)
   * [Setting some effects for skin](/docs/guide/skinconfig/CharacterConfig.md)









<br><br><br><br><br><br><br>



not edited yet 


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
