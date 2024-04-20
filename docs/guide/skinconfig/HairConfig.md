---

## HairConfig.yaml

---

If you need to customize hair color and related attributes for specified IDs in the Sprites.xml, follow these instructions.

To utilize these configurations, you'll need to create a new configuration file for the object ID, structured as follows: "../Gameplay/[ID's root path]/skinConfig/HairConfig.yaml"

Below is the template for this new config file.

```yaml
  HairLengths:
  - < HairLength >
  HairColors:
  - < HairColor >
  HairFlash: [true/false]
  OutlineColor: [use six-digit RGB hex code]
```

---

### HairLengths

If you wish to adjust the length of the hair for the object ID, use this configuration:

```
  HairLengths:
  - Dashes: [use -1 to 32]     
      # Using [-1] applies this length to the player in feather status
    Length: [use 1 to 99]
```

---

### HairColors

To assign a new hair color to the object ID, different from Maddy's default color, follow this setup:

```
  HairColors:
  - Dashes: [use 0 to 32]
    Color: [use six-digit RGB hex code]     # Example: "9B3FB5", which represents Baddy's 1-dash color
    SegmentsColors:
    - Segment: [Specify hair segments]     # Use negative numbers for reverse order
      Color: [use six-digit RGB hex code]
```

---

### HairFlash

By default, the player's hair flashes when dashes are used or refilled. If you wish to disable this feature, use:

```
  HairFlash: false
```

---

### OutlineColor

If you need to recolor the hair border of the object ID, use this configuration:

```
  OutlineColor: [use six-digit RGB hex code]
```

[Previous Page](/docs/guide/README.md#more-miscellaneous)

---
