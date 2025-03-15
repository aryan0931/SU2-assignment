# **Building and Running SU2**  

## **1. Cloning the Repository**  
To get started, clone the SU2 repository from GitHub:  
```bash
git clone https://github.com/su2code/SU2.git
cd SU2
```

## **2. Compiling SU2**  
SU2 can be compiled with different options. Below are some common configurations:

### **Basic Compilation**
```bash
mkdir build && cd build
cmake ..
make -j$(nproc)
```

### **With MPI Support (For Parallel Runs)**
```bash
mkdir build && cd build
cmake .. -DENABLE_MPI=ON
make -j$(nproc)
```

### **With Python Wrapper Support**
```bash
mkdir build && cd build
cmake .. -DENABLE_PYTHON=ON
make -j$(nproc)
```

### **With AD Support (For Adjoint Solver)**
```bash
mkdir build && cd build
cmake .. -DENABLE_AD=ON
make -j$(nproc)
```

After a successful build, SU2 executables will be available in the `build/bin/` directory.

## **3. Running SU2 Tutorials**
Once compiled, you can test your installation by running example cases from the SU2 tutorials.  
Here are some examples:

### **Running a Simple NACA 0012 Airfoil Case**
```bash
cd ../TestCases/euler/naca0012
../../build/bin/SU2_CFD inv_NACA0012.cfg
```

### **Running a Turbulent Flat Plate Case**
```bash
cd ../TestCases/turbulence/flat_plate
../../build/bin/SU2_CFD turb_flatplate.cfg
```

### **Running in Parallel (MPI Example)**
```bash
mpirun -np 4 ../../build/bin/SU2_CFD turb_flatplate.cfg
```

![Screenshot 2025-03-15 at 1 55 43 PM](https://github.com/user-attachments/assets/6f2a28e4-1962-42da-b78d-e7243784459f)
