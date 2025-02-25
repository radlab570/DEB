# DEB
**DEB** -- Direct Estimation of Bones -- is a workflow for putting pre-recorded motion capture animations in Unreal Engine.

### Highlights
- Created from a video
- Automatic creation of skeletal mesh and animation
- Easy import into Unreal

### Necessary Tools
- QuickMagic.ai
- Unreal Engine 4+

## Steps For Implementing In Unreal
1. Import your video animation into QuickMagic.ai.
    - For best results, your video should only have one person visible and in focus.
2. Follow the instructions from QuickMagic.ai until you get to the export option.
3. Choose the Unreal Engine option for exporting.
4. Once the video is processed, download the animation.
5. Extract the ZIP file to find the FBX file.
6. Open an Unreal Engine project.
7. Navigate to "File" > "Import Into Level..." > and select the FBX file.
8. Select where you want the files to save to in the Content Drawer.
9. In the "FBX Scene Import Options" window, under the "Import Options" dropdown menu, select the "Import as Dynamic" option as True. Finally, select import.
10. To have the model do the animation when the game starts complete the following steps:
    - Open the Blueprint Class of the model.
    - Open the Event Graph
    - From the "Event BeginPlay" node, insert a "Play Animation" node.
    - In the "New Anim to Play" option, select the animation sequence for the model.
    - You can loop the animation by clicking the "Looping" boolean as True.
