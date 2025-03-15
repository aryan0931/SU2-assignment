### **Task Description**
The task involved setting up and running SU2 regression tests to verify the correctness of the SU2 installation and ensure the accuracy of simulations. This included:

1. **Cloning Repositories**: Downloading the SU2 source code, Testcases, and Verification & Validation (V&V) repositories.
2. **Organizing Files**: Structuring the directories to ensure the test cases and meshes were accessible.
3. **Building SU2**: Compiling SU2 from source using CMake and Make.
4. **Setting Up Environment**: Configuring environment variables to enable seamless execution of SU2 and its regression tests.
5. **Running Tests**: Executing both serial and parallel regression tests to validate the installation.
6. **Analyzing Results**: Verifying that all tests passed, confirming the installation was successful and ready for use.

The goal was to ensure that SU2 was correctly installed and capable of producing accurate results for various test cases, including compressible flow simulations.

--- 

# SU2 Regression Test Setup

This repository documents the setup and execution of SU2 regression tests to verify the installation and functionality of SU2.

## Steps Performed

1. **Cloned Repositories**:
   - SU2: `git clone https://github.com/su2code/SU2.git`
   - Testcases: `git clone https://github.com/su2code/Testcases.git`
   - Verification and Validation (V&V): `git clone https://github.com/su2code/vandv.git`

2. **Organized Files**:
   - Moved `Testcases` and `vandv` folders into the `SU2` directory for proper structure.

3. **Built SU2**:
   - Created a `build` directory and compiled SU2 using CMake:
     ```bash
     mkdir build
     cd build
     cmake .. -DCMAKE_INSTALL_PREFIX=$SU2_HOME
     make -j4
     make install
     ```

4. **Set Up Environment Variables**:
   - Added SU2 to `PATH` and `PYTHONPATH`:
     ```bash
     export PATH=$SU2_HOME/bin:$PATH
     export PYTHONPATH=$SU2_HOME:$PYTHONPATH
     ```

5. **Ran Regression Tests**:
   - Executed serial and parallel regression tests:
     ```bash
     python serial_regression.py
     python parallel_regression.py
     ```

6. **Verified Results**:
   - All regression tests passed, confirming a successful SU2 installation.

---

## Notes
- Python 3 and MPI were used for running the tests.
- Ensure all dependencies (e.g., `numpy`, `scipy`) are installed before running the tests.

---


---

This `README.md` is concise and clearly documents your work. You can place it in the root of your SU2 directory or in a separate folder for documentation. Let me know if you need further adjustments! 😊
![Screenshot 2025-03-15 at 3 00 13 PM](https://github.com/user-attachments/assets/08571ab1-24d3-44cf-bc08-302140de7a1c)
![Screenshot 2025-03-15 at 3 00 37 PM](https://github.com/user-attachments/assets/c58f0386-a018-4a66-b302-9a7cc3a95164)
![Screenshot 2025-03-15 at 3 01 10 PM](https://github.com/user-attachments/assets/28beaa54-10b7-490c-acd4-d2979e56423e)
