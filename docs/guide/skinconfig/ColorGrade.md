---

## ColorGrades

---

Color grades allow you to change the colors of a specified sprite ID's texture based on the dash counts of the ID itself. To implement them, follow these steps:

1. Create a folder for the specified ID, structured like so: `../Gameplay/[ID's root path]/ColorGrading/`

2. Within that folder, name the images as "dash[X].png", where [X] represents the number of dashes the color grade should be applied to.
   - For instance, if you require a color grade for a 0-dash scenario, name the file "../Gameplay/[ID's root path]/ColorGrading/dash0.png"
   - You can obtain the base color grade from "Celeste/Content/Graphics/ColorGrading/none.png"

3. Select the color you wish to replace on the sprite of the specified ID, locate that color on the color grade image, and substitute it with the desired color for that dash count.

Following these steps completes the setup of color grades for the specified ID.

---

### Additional Notes

- You have the option to include an extra color grade named "flash.png". It will take effect when the player's hair flashes.
- Color grades also function for NPC Badeline.
- Please note that color grades don't support CelesteNet yet.

[Previous Page](/docs/guide/README.md#more-miscellaneous)

---
