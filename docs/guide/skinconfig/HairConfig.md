
HairConfig.yaml
-----------------------------------
Here you can change hair related settings for your character.
In fact, you can change the hair for any Sprite-ID specified in Sprites.xml, if it has hair.

These settings are located in a new config file. Create the new config file at the path: <br>
`"../Gameplay/[ID's rootPath]/skinConfig/HairConfig.yaml"`

Here is a skeleton of that new config file. 
Each of the fields will be explained below.
```yaml
  HairLengths:
  - < HairLength >
  HairColors:
  - < HairColor >
  HairFlash: [true/false]
  OutlineColor: [use six digit RGB hex code]
```

HairLengths
-----------------------------------
You can change you character's hair length.
```yaml
  HairLengths:
  - Dashes: [use -1 to 32]     
      # use [-1] to change the feather trail length.
    Length: [use 1 to 99]
```

HairColors
-----------------------------------
You can change your character's hair color. SegmentsColor option is optional and can override the color for specific hair segments. (like the pattern option in hyperline)
```yaml
  HairColors:
  - Dashes: [use 0 to 32]
    Color: [use six digit RGB hex code]     # such as: ["9B3FB5"], that is badeline's 1-dash color
        SegmentsColors: (optional)
        - Segment: [Which segments of hair]     # use negative numbers to get reverse order
          Color: [use six digit RGB hex code]
```

HairFlash
-----------------------------------
You can enable / disable the white flash that happens when your dash count changes.
```yaml
  HairFlash: false
```

OutlineColor
-----------------------------------
You can change the outline color of the your character's **hair**.
```yaml
  OutlineColor: [use six digit RGB hex code]
```


[previous page](/docs/guide/README.md#more-miscellaneous)
