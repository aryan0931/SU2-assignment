
## 1. Enabling a Spatially Varying Wall Temperature in the Python Wrapper

Suppose the original Python wrapper simply reads a constant wall temperature from the configuration. We modify it so that a user can supply a spatial function. For example:

```
import pysu2
from math import sin, pi
from mpi4py import MPI

def main():
    comm = MPI.COMM_WORLD

    # Initialize SU2 driver
    try:
        SU2Driver = pysu2.CSinglezoneDriver('turb_SA_flatplate.cfg', 1, comm)
    except TypeError as exception:
        print('A TypeError occurred in pysu2.CDriver:', exception)
        raise

    # Get the marker ID for 'wall'
    AllMarkerIDs = SU2Driver.GetMarkerIndices()
    MarkerName = 'wall'
    MarkerID = AllMarkerIDs.get(MarkerName, -1)

    if MarkerID >= 0:
        # Get number of vertices and marker coordinates
        nVertex = SU2Driver.GetNumberMarkerNodes(MarkerID)
        marker_coords = SU2Driver.MarkerCoordinates(MarkerID)

        # Apply spatially varying wall temperature
        for i_vertex in range(nVertex):
            x = marker_coords[i_vertex][0]  # ✅ Fixed indexing
            WallTemp = 560.0 - 260.0 * sin(x * pi / 4)
            SU2Driver.SetMarkerCustomTemperature(MarkerID, i_vertex, WallTemp)

    # Run the solver
    SU2Driver.StartSolver()
    SU2Driver.Finalize()

if __name__ == '__main__':
    main()
```

*Notes:*
- You may need to adjust how boundary locations are stored/used.
- This example assumes the configuration dictionary includes coordinates or that you can compute a representative point for each boundary.

---

