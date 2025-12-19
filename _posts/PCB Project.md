---
title: "PCB Project" 
categories:
    -Tutorials
    -Blogs
tags: 
    -markdown
    -github
    -pages

---

# Daily Journal

Day 1: We were introduced to MakeraCam and learned how to do the toolpaths for the file. We had to make a workflow as we went along and then after we had to make the g-code without help from our teacher. 

Days 2-4: We learned how to use the new CNC machines to mill our PCB boards. This took multiple days due to our class size. When we were waiting for our turns we worked on our personal projects and documentation. 


# MakeraCam Workflow

1. Open up Makera CAM and start a new 3-axis project.

![PCB Image](/assets/images/IMG_1568.jpg)

2. Then we need to import the PCB files. These files are the .grb & .drl files.

![PCB Image](/assets/images/Step2.png)

![PCB Image](/assets/images/Step2.2.png)

3. Files will then appear under WCS1

![PCB Image](/assets/images/Step3.png)

4. Once all our files are in the software, they will likely not be in the correct position, so we 
need to move them to have the bottom left of the files 6mm offset in both the x and y axes. 

![PCB Image](/assets/images/Step4.png)

5. Click and drag over the entire file, which should turn into dotted lines when selected. Then go to the transform tool, or use the keybind “m” to open the move menu. Finally, make sure the bottom left dot in the menu is selected and set both the x and y to 6mm.

![PCB Image](/assets/images/Step5.png)

6. Now that the files are in place, it’s time to start telling the CNC machine how to cut each part, starting with the traces. The key to making toolpaths in MakeraCAM is to effectively manage which layers are hidden to click and drag over only what needs to be selected. For the traces, we want to hide all layers except the following: FileName-F_Cu.grb & FileName-Edge_Cuts.grb . You might notice that there are .grb_pad files, but we will never use these, so keep them hidden so as not to accidentally select them.

![PCB Image](/assets/images/Step6.png)

7. When only the 2 main files, F_Cu and Edge_Cuts, are visible, click and drag over the entire area to select everything. Then, zoom in on one of the edges of the Edge_Cut file and deselect the outermost layer of the edge cut. Note that while it looks like a single line zoomed out, it actually is two offset lines.

8. Once the selection is all correct, go up to the top menu and select the 2D paths icon, which looks like an arc with a horizontal tangent line. 

![PCB Image](/assets/images/Step8.png)

9. When clicked, a dropdown should appear with a choice for 2D Pocket; select that option. Note that the selection from the previous step should still be active and selected. For the settings, set the End Depth to 0.05mm, Retract to 5mm(for faster cutting).

![PCB Image](/assets/images/Step9.png)

10. Click on the button “Add Tool” and select the .8mm Corn, click select on the bottom right of that menu.

![PCB Image](/assets/images/step10.png

11. Do the same for adding the .2mm 30* Engraving Bit(make sure PCB is selected below the Bit Selection menu.).

![PCB Image](/assets/images/Step11.png)

12. Finally, click calculate at the bottom, and the toolpath should generate. If you would like to hide it until later, it can be hidden using the left menu under the layers area.

![PCB Image](/assets/images/Step12.png)

13. Once the PCB traces are cut, we need to add the holes if your design has any. If your file has no .drl files, then skip this step. If it does have .drl files, then we need to go into the 2D path icon dropdown and select 2D drilling.

![PCB Image](/assets/images/Step13.png)

14.  In the 2D drilling menu, click on the Choose Tool button and select the .8mm Corn mill bit, the same bit we used to cut the traces. Ensure that PCB is still highlighted in the bottom menu of the selection box when the .8mm corn is selected. 

15. Once the tool is selected, set the depth of the drilling to 1.7mm, which is the depth of the PCB board. Then scroll to the bottom of the menu and click calculate. 

16. Once the PCB holes are cut, we can then cut the board out of the big copper sheet by cutting along the Edge cut line. However, unlike with traces where we used a 2D pocket, we will instead use a 2D contour cut to only cut along the edge line of our file. Similarly to the traces, select the inside line of the Edge Cut file.

![PCB Image](/assets/images/Step16.png)

17.  Once selected, go to the 2D paths icon used before and select 2D Contour.

![PCB Image](/assets/images/Step17.png

18. Once selected, select the .8mm corn mill bit as the tool, and ensure PCB is still 
highlighted in the bottom menu of the selection box when the .8mm corn is selected. 

![PCB Image](/assets/images/Step18.png)

19. Once the tool and vectors(edge cut lines) are selected, choose outside as the path of travel to account for the width of the .8mm bit.

![PCB Image](/assets/images/Step19.png)

20. Finally, before we calculate this cut file, we need to make sure that the board won’t come loose mid-cut and potentially fly into the bit. We can do this by using Tabs, essentially small areas of the cut area, which we will skip over to keep the milled PCB board attached to the big copper plate. To add these tabs, scroll to the bottom of the 2D Contour menu and select the circle labeled custom under the Tabs header. Then, click on the button labeled “Add” and select where you want to add Tabs. Typically, you want at least 3 tabs distributed equally on the cut, but this can vary depending on the size and shape of the board.

![PCB Image](/assets/images/Step20.png)

21.  Once the tabs have been added, which is shown by a square with an X in it, you can finally click calculate, and the cut file is complete

![PCB Image](/assets/images/Step21%20.png)

22.  Yay, the board is complete! Now all that is left is to preview and export the toolpaths so that the CNC machine can cut them. To preview the toolpath before cutting, select the preview toolpath icon in the upper menu, which looks like a sheet of paper with a magnifier glass on it. 

![PCB Image](/assets/images/Step22.png)

23. Select this icon and check the boxes for all the toolpaths shown.

![PCB Image](/assets/images/Step23.png)

24. Click the play icon at the bottom to watch the cut preview. The speed of the preview can be adjusted using the slider under the play button, and the upper-right menu box labeled Preview Toolpaths changes what is seen in the preview.

![PCB Image](/assets/images/Step24.png)

25. Click exit preview

![PCB Image](/assets/images/Step25.png)

26. Export the file 

![PCB Image](/assets/images/Step26.png)

27. Select all toolpaths

![PCB Image](/assets/images/Step27.png)

28. Name file [LastnameResistorgcode] and save file as a g-code

![PCB Image](/assets/images/Step28.png)


# Initial Files Provided

![PCB Image](/assets/images/Resistance1-Edge_Cuts.gbr)


# Final PCB Board G-Code

![PCB Image](/assets/images/Board.nc)


# Final PCB Board

This was the board that I milled in class using the new CNC machines. We first had to learn how to use MakeraCam and write a workflow. Then we learned how to use the new CNC machines. Then we designed our board and milled it, as shown in the photo.
![PCB Image](/assets/images/FinalPCB.png)


# Problems Encountered

The process ran very smoothly for me and my partner, Raaj Thakur. The only issues I encountered were at the beginning with uploading the template files to MakeraCam. The files did not upload with the correct format, so I had to restart the software and start again. MakeraCam was also prone to crashing and random points, but the solution there was just to reopen the software. 


# Summary

This project was a chance for us to learn new skills that could be applied to our personal projects later on. We learned how to create a g-code in MakerCam and then we leanred how to use the new CNC machines in the lab. Now for our personal projects we would be able to mill our own boards for the electronics. The project allowed us to troubleshoot and learn from our mistakes in a small scale environment. 