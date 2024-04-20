---

## CharacterConfig.yaml

---

If you wish to apply certain effects to your target, you can configure them here.

This section outlines a new configuration file along with its structure and functions:

```yaml
SilhouetteMode: [true/false]

LowStaminaFlashHair: [true/false]
LowStaminaFlashColor: [use six-digit RGB hex code]

TrailsColor: [use six-digit RGB hex code]
DeathParticleColor: [use six-digit RGB hex code]
```

If this contains what you need, follow these steps to use them:

1. Navigate to the directory of the target sprite.
2. Create a new folder named `skinConfig` here.
3. Place a file named "`CharacterConfig.yaml`" within the "`skinConfig`" folder.
   - Example path: `../Gameplay/[target sprite's directory]/skinConfig/CharacterConfig.yaml`
4. Copy the fields you need and specify their values in `CharacterConfig.yaml`.
   - For field details, refer below.

---

### SilhouetteMode

If you want to color the entire target's sprites with its hair color, resembling a silhouette effect, use this configuration:

```
SilhouetteMode: true
```

Note: This also affects the target's hair border color, defaulting to black.

---

### LowStaminaFlash

When the player's stamina is nearly depleted, the player will start flashing red. To customize this flash color (if it's too intense for your skin), utilize this setting:

```
LowStaminaFlashColor: [use six-digit RGB hex code]     # default color is "ff0000"
```

If you want this flash effect to apply to the skin's hair as well, use:

```
LowStaminaFlashHair: true
```

---

### TrailsColor

Certain entities will generate trails at times, such as birds, Oshiro bosses, and seekers. To recolor these trails, use:

```
TrailsColor: [use six-digit RGB hex code]
  # If the target is Badeline Chaser, you can set this to a special "HairColor"
```

Note: This is not applicable for players or silhouettes.

---

### DeathParticleColor

Some entities generate death particles with their color. To recolor these particles, use:

```
DeathParticleColor: [use six-digit RGB hex code]
```

[Previous Page](/docs/guide/README.md#more-miscellaneous)

---
