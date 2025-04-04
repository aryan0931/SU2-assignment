I have successfully implemented the addition of the local speed of sound in the volume output (ParaView files) and the screen output within SU2.

Implementation Details:
Modified the SU2 solver to compute and store the local speed of sound at each grid point.
Integrated this computation into the volume output, ensuring it is available in the ParaView files for visualization.
Updated the screen output to display the computed local speed of sound during the simulation run.
Verification:
Ran the turbulent test case from point 2 with the updated volume and screen output enabled.
Verified the screen output by checking the history file for the new local speed of sound values.
Generated visualization images from ParaView showing the distribution of the local speed of sound in the computational domain.
