Objective
Simulate a steady-state oblique shock using the Euler equations (inviscid flow) to study compressible flow behavior under supersonic conditions.

Key Configurations
Flow Physics:

Solver: EULER (inviscid flow, no turbulence).

Freestream: Mach 3 flow, temperature = 300 K, pressure = 101325 Pa (ambient conditions).

Fluid Model: Ideal gas (GAMMA_VALUE = 1.4, GAS_CONSTANT = 287.0).

Boundary Conditions:

Supersonic Inlet: Velocity = 1041.57 m/s (aligned with Mach 3), temperature/pressure specified.

Supersonic Outlet: Flow variables extrapolated from interior (no back pressure imposed).

Wall: Inviscid slip condition (no boundary layer effects).

Numerical Methods:

Convective Scheme: HLLC (robust for shocks).

Time Integration: Implicit Euler (TIME_DISCRE_FLOW = EULER_IMPLICIT).

Convergence: Monitors density residuals (CONV_FIELD = RMS_DENSITY) with adaptive CFL.

Convergence & Output:

Iterations: 1000 outer iterations for steady-state convergence.

Outputs: ParaView files every 100 iterations for visualizing flow fields (pressure, temperature, etc.).

Restart Files: Saved to restart.dat.

Expected Results
A stationary oblique shock wave at 13°, caused by the geometry (e.g., a wedge).

Shock properties like angle, pressure/temperature jumps, and Mach number reduction downstream.

Visualizations: Shock structure, Mach contours, and pressure gradients in ParaView.

![Screenshot 2025-03-15 at 2 23 35 PM](https://github.com/user-attachments/assets/a7335630-bd62-40ad-bae6-7c0e49a10bf2)

![Screenshot 2025-04-02 at 10 15 03 AM](https://github.com/user-attachments/assets/4fcebca2-07e1-49c4-9d11-81aa84032ad2)

