
CharacterConfig.yaml
-----------------------------------
You can use this file to set some special effects for your character.

These settings are located in a new config file. Create the new config file at the path: <br>
`../Gameplay/[ID's rootPath]/skinConfig/CharacterConfig.yaml`

Here is a skeleton of that new config file. 
Each of the fields will be explained below.

```yaml
BadelineMode: [true/false]
SilhouetteMode: [true/false]

# ---yes, this config only has those two options currently---
```


Character's effect setting
-----------------------------------
If you want to set it's character-effect for object-ID, 
Then you can choose to add the effect you want (you can add multiple):
```
BadelineMode: [true/false]     # if true: Use badeline's hair color.
SilhouetteMode: [true/false]     # if true: Color the character's entire body with its hair color, like a the playback sprite.
```



[previous page](/docs/guide/README.md#more-miscellaneous)
