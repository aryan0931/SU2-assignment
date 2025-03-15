
## 1. Enabling a Spatially Varying Wall Temperature in the Python Wrapper

Suppose the original Python wrapper simply reads a constant wall temperature from the configuration. We modify it so that a user can supply a spatial function. For example:

### **Before Correction (Original Setup)**
```python
# Original snippet from setup.py (simplified)
def setup_boundary_conditions(config):
    # For each wall boundary, use the constant wall temperature
    for boundary in config['boundaries']:
        if boundary['type'] == 'wall':
            # Use constant temperature from the config
            boundary['temperature'] = config.get('WALL_TEMPERATURE', 300)
```

### **After Correction (Spatially Varying Wall Temperature)**
```python
import math

def wall_temperature_profile(x, y, z):
    """
    Example spatial function for wall temperature.
    Modify this function based on physical requirements.
    For instance, temperature could vary linearly with x.
    """
    # Base temperature plus an increase proportional to x.
    base_temp = 300  # Kelvin
    gradient = 10    # Kelvin per unit length
    return base_temp + gradient * x

def setup_boundary_conditions(config):
    # For each wall boundary, assign a spatially varying temperature.
    for boundary in config['boundaries']:
        if boundary['type'] == 'wall':
            # Assume each boundary has a representative location (x, y, z).
            x = boundary.get('x', 0)
            y = boundary.get('y', 0)
            z = boundary.get('z', 0)
            # Use the spatial function to compute the temperature.
            boundary['temperature'] = wall_temperature_profile(x, y, z)
```

*Notes:*
- You may need to adjust how boundary locations are stored/used.
- This example assumes the configuration dictionary includes coordinates or that you can compute a representative point for each boundary.

---

## 2. Addition of New Volume Output: Local Speed of Sound

In the SU2 C++ code, assume that the output routines for volume data (used for Paraview visualization) need to include the local speed of sound. The speed of sound is typically computed as:

\[
a = \sqrt{\gamma \, R \, T}
\]

Where:
- \( \gamma \) is the heat capacity ratio,
- \( R \) is the specific gas constant, and
- \( T \) is the local temperature.

### **Before Correction (Original Output Routine)**
```cpp
// Simplified snippet from the volume output routine
void OutputVolumeData(const Mesh &mesh, const FlowSolution &sol, std::ostream &outputFile) {
    for (const auto &cell : mesh.cells) {
        // Existing outputs: pressure, velocity, temperature, etc.
        outputFile << cell.id << " " << sol.pressure[cell.id] << " " << sol.temperature[cell.id] << "\n";
    }
}
```

### **After Correction (With Speed of Sound)**
```cpp
#include <cmath>

// Assume gamma and R are defined either as constants or read from the configuration.
const double gamma_val = 1.4;
const double gas_constant = 287.0;

void OutputVolumeData(const Mesh &mesh, const FlowSolution &sol, std::ostream &outputFile) {
    for (const auto &cell : mesh.cells) {
        double T = sol.temperature[cell.id]; // Local temperature
        // Compute local speed of sound: a = sqrt(gamma * R * T)
        double local_speed_of_sound = std::sqrt(gamma_val * gas_constant * T);

        // Output cell id, pressure, temperature, and local speed of sound.
        outputFile << cell.id << " " 
                   << sol.pressure[cell.id] << " " 
                   << T << " " 
                   << local_speed_of_sound << "\n";
    }
}
```

### **Updating Screen Output (History File)**
In addition to volume output, you might also want to update the screen output (history log) to include the local speed of sound. For example:

#### **Before Correction (Screen Output)**
```cpp
// Simplified snippet from the history output function
void OutputScreenData(const FlowSolution &sol, int iteration) {
    std::cout << "Iteration: " << iteration 
              << " | Residual: " << sol.residual 
              << " | Lift: " << sol.lift 
              << "\n";
}
```

#### **After Correction (Screen Output with Speed of Sound)**
```cpp
void OutputScreenData(const FlowSolution &sol, int iteration, double avgTemperature) {
    // Compute average local speed of sound from avgTemperature.
    double avg_speed_of_sound = std::sqrt(gamma_val * gas_constant * avgTemperature);
    
    std::cout << "Iteration: " << iteration 
              << " | Residual: " << sol.residual 
              << " | Lift: " << sol.lift 
              << " | Local Speed of Sound: " << avg_speed_of_sound
              << "\n";
}
```

*Notes:*
- The average temperature for screen output can be computed over all cells or over a region of interest.
- Adjust variable names and locations as necessary to match your SU2 code structure.

---

### Summary of Code Corrections

- **Python Wrapper Modifications:**  
  - Added a function (`wall_temperature_profile`) to compute spatially varying wall temperature.
  - Modified the boundary condition setup to use the new spatial function.

- **C++ Modifications for Volume Output:**  
  - Added a computation of local speed of sound in the volume output routine.
  - Updated the screen output routine to include a new column for the average local speed of sound.
