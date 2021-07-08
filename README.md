# ivy_growth_animator
## Blender Addon that animates the growth of trees and ivy
## Wiki

## Add-on Description:

This add-on animates the growth of ivy and trees created by the ivy generator and sapling add ons. It can animate other objects as well, but will only work with “branches” that are made of a single curve object, even if it’s made of separate “loose parts”. It will also produce decent results only if the curves have been created in an ascending or descending order, for instance with the bottom branch being first, and higher branches created later and by order of height.
The curves representing the branches are converted to meshes by the add on.

For the leaves animation, it also requires that the leaves will be composed of a single mesh object, with each leaf being a separate, loose face.

The add on uses the Build modifier to animate the branches, and shape keys to animate the leaves.

## Warning!

To animate the leaves, the add on creates a shape key for each face on the leaves mesh. If you have many leaves (over a few hundred), this can take several minutes (depending on your computer), and even several hours (!!) if you have thousands of leaves. The process also gets slower with each additional shape key. So splitting the mesh into several different objects is better than trying to do many leaves all at once.
I will probably optimize this in the future, but at the moment its not a very viable solution for a huge amount of leaves (over a few thousand) all in one mesh.

## General usage:

To use the add on with the default parameters:
1. choose the name of the curve object and place it in the “BranchObject” object selection box.
1. Press on the “Animate Branches” Button.
1. Choose the leaves mesh object, and place its name in the “LeavesObject” object selection box.
1. Make sure you have the correct “BranchObject” name as well, alongside the “LeavesObject” name.
1. Press the “Animate Leaves” button.
1. Play the animation and enjoy!

### Notes:
1. The “BranchObject” name must be unique. If another object is too similar (contains the BranchObject’s name) the script will fail with an error.
1. To animate the leaves you must first animate the branches.
1. The leaves use the branch animation data to time the appearance of each leaf. So to get the proper results, you must have the correct “BranchObject” name in the box alongside the “LeavesObject” before pressing the “Animate Leaves” button.

### Add-on parameters:
* __BranchObject__ – name of the curve object which represents the branches.
* __LeavesObject__ – name of the mesh object that represents the leaves.

### Branch Animation Parameters:
* __frame_start__: the start frame for the animation of the branches.
* __faces_per_frame__: the speed of the branch building animation. The higher the number, the faster the animation. Technically, it represents the number of faces that are built in one frame.
* __delay_branches__: the number of frames to wait before starting to animate the next branch. Also determines the overall speed of the animation, and helps coordinating it.
* __initial_delay__: The first branch is often large and needs more time before the next one should start. This parameter helps you set a delay between the first and second branches to help coordinate this.

### Leaves  animation parameters:
* __delay_after_branch__: how long (how many frames) to wait after the closest branch to the leaf finished animating, before starting to animate the leaf.
* __max_growth_length__: the maximum number of frames (length) for animating the growth of a leaf. The total length will be randomly set between this value and the “min_growth_length” value.
* __min_growth_length__: the minimum number of frames (length) for animating the growth of a leaf. The total length will be randomly set between this value and the “max_growth_length” value.

