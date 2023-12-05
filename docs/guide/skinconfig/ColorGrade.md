
ColorGrades
-----------------------------------
This config is used to set custom color grades for specified-ID in Sprites.xml.

colorGrades will make specified-ID are rendered differently at different dash counts of IDself.

You can create a custom colorgrade like this:

1. create a folder for the specified-ID：`../Gameplay/[IDself's rootPath]/ColorGrading/`

3. in that folder, name the images `dash[X].png`, where [X] is the number of dashes the color grade should apply to.
   * For example, if you had a 0-dash color grade, you would name the file `../Gameplay/[IDself's rootPath]/ColorGrading/dash0.png`
   * You can grab the base game's color grades from `Celeste/Content/Graphics/ColorGrading/none.png`
    
4. Pick the color you want to replace on the sprite of specified-ID, find that color on the color grade, and then replace it with the color you want for that dash count.


more things
-----------------------------------
* color grades work on the NPC badeline, you can to test it if you want to.
* color grades aren't supported on CelesteNet yet.


[previous page](/docs/guide/README.md#more-miscellaneous)
