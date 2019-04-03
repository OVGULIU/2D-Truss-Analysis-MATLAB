2D Truss Analysis script for MATlab
===================================

This is a rough draft of a 2D truss analysis script.  

To Install: Download the .zip of the entire folder, and extract to a computer that has matlab installed.

To run: make sure your current directory is set to the loaction of the file _TrussGui.m_ and in the command prompt run:

       TrussGui

A pop up will ask you for the dimensions of your truss, in order to create the grid that will be used.

1) _Add Members_
	Draw the truss by clicking on the "Add Members" button.  Each member can be drawn by clicking two points on the grid.  Note: The total number of members must be equal to 1/2 the number of joints minus 3. Failure to comply will result in an instable or indeterminate truss, and will result in errors.

Retrace a member to delete it.

_When finished adding all members, click the "return" key._

2) _Add Supports_
	Click the "Add Supports" button, and the script will ask you first to choose the loaction of the pin support and next to determine the location of the roller support.  Currently, the roller support will only provide a vertical reaction.

3) _Add Loads_
	Add loads to the truss by clicking on the "Add Loads" button.  A popup will ask for the x and y component of the force applied to that joint.  

To edit a load, click on the joint again.

When finished adding all loads, _click the "return" key_.

4) _Analyze_
	Click "Analyze" to compute the loads in each member. Members in Tension will appear blue, and have positive values, members in compression will appear red and have negative values. Zero-force members will be black. 

5) _Iterate_ - at any time you can change your confiurguation by clicking the approprate button.

## Technical Notes (How it all works)

This code looks big and messy, but mostly this is from creating the graphical user interface. What it's doing underneath the hood is:

Building a `struct` data type that contains the following fields:

  * `trussMembers` is an array of the x and y start and end points of all members of the truss.
  * `trussSuports` contains the x and y coordinates of the pin and roller supports, respectively
  * `trussLoas` contains the x and y coordnates and x and y magnitudes of applied loads

  The code then fills in the matricies A and B