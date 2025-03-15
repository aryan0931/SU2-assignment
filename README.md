# SU2 Assignments

This repository documents the completion of SU2-related assignments, focusing on compiling SU2, setting up test cases, modifying the Python wrapper, adding new volume outputs, and running regression tests.

---

## **Assignments Completed**

### **Compile SU2**
- Cloned SU2 from GitHub and compiled it with different options.
- Ran tutorials to verify the installation.
- **Deliverable**: None.

### **Set Up a Test Case from Scratch**
- Generated a 2D mesh for an axisymmetric, steady-state, turbulent jet case using GMSH.
- Set up the configuration file and ran the simulation.
- Extracted results and compared them with experimental values from the reference paper:


### **Modification of the Python Wrapper Setup**
- Enabled a spatially varying wall temperature for a steady-state compressible turbulent flat plate test case.
- **Deliverable**: Test case and a small report describing the results.

### **Addition of New Volume Output**
- Added the local speed of sound as computed by SU2 to the volume output (Paraview files) and screen output.
- Ran the turbulent test case from the axisymmetric jet case with the new volume and screen output enabled.
- **Deliverable**: Explanation of the implementation, history output of the new screen output, and images of the volume output.

### **Regression Test Setup**
- Combined the configuration files from `SU2/TestCases` with the meshes from the `TestCases` repository.
- Executed `serial_regression.py` and `parallel_regression.py` without any issues.
- **Deliverable**: Confirmation that all regression tests passed successfully.

---

## **Repository Structure**
- **Compile_SU2**: Compiled SU2 and ran tutorials.
- **Test_Case_Setup**: Contains the 2D mesh, configuration file, simulation results, and report for the axisymmetric turbulent jet case.
- **Python_Wrapper_Modification**: Modified Python wrapper setup for spatially varying wall temperature.
- **Volume_Output_Addition**: Added speed of sound output and updated test case results.
- **Regression_Tests**: Configuration files and results from running regression tests.

---

## **Message to Supervisor**
Hello Sir,  
As per your instructions, I've successfully set up and run the regression tests. I combined the configuration files from `SU2/TestCases` with the meshes from the `TestCases` repository and executed `serial_regression.py` and `parallel_regression.py` without any issues. Everything seems to be working as expected.

---


## **References**
- SU2 GitHub Repository: [https://github.com/su2code/SU2](https://github.com/su2code/SU2)
---

For questions or issues, feel free to reach out!

---
