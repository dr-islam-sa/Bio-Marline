# Bio-Marlin V1.2 (Beta) 💻
Open Source 3D Bioprinter firmware based on open source project Marline V1.1.9 | modified by Dr.Islam Salama 
| Linkedin https://www.linkedin.com/in/dr-islam-sa


# Bio-Marlin V1.2 (Beta) 

### Overview
**Bio-Marlin V1.2** is a modified firmware based on **Marlin 1.1.9**, optimized specifically for 3D bioprinting applications. This project redefines certain features of the original firmware, removing nonessential components and introducing functionalities necessary for precise, bio-compatible printing. Bio-Marlin focuses on enabling the handling of unique materials, like hydrogels, by offering advanced control over extruder speed and temperature, thereby supporting the bioprinting community in experimenting with diverse bio-materials and advancing biotechnology research.

> **Note**: Bio-Marlin V1.2 is in beta. It is a community-driven project, and all contributions are welcome to help enhance the firmware for future versions.

---

## Key Features and Enhancements
Bio-Marlin is carefully adapted for bio-compatible 3D printing. Key modifications include:

1. **Minimized Firmware for Efficiency**:
   - **Removed Language and Screen Files**: Bio-Marlin excludes multilingual support and unused display files to reduce firmware size and complexity, optimizing it for bioprinting needs.
   - **Stripped-Down Interface**: Only essential menus and commands are available, enabling a streamlined setup and eliminating features irrelevant to bio-based applications.

2. **Bioprinting-Specific Modifications**:
   - **Extruder Speed Control**: The extruder speed can be finely adjusted to manage material viscosity, a critical factor for bio-inks and hydrogels. This modification is essential for maintaining consistent extrusion of varying bio-materials.
   - **Enhanced Bed Size Configuration**:
     - **Small Print Area**: The print bed size is set to 8x8 cm, a scale appropriate for many bioprinting applications focused on tissue scaffolds, cell patterns, and other small biofabrications.
   - **Temperature Optimization for Hydrogels**:
     - **Modified Nozzle Function**: In place of heating for extrusion, the nozzle temperature controller now supports cooling for hydrogel storage during printing, with a strict limit of 23°C to ensure temperature-sensitive materials remain viable.

3. **License Compliance and Open Source Commitment**:
   - This project honors Marlin’s original open-source license, offering a free-to-use, customizable firmware that respects the ethos of open science.
   - Bio-Marlin does not resell or rebrand the Marlin firmware, aiming solely to foster scientific growth in biotechnology and bioprinting.

---

## Detailed Specifications

### 1. Extrusion Control for Viscosity Management
   - **Dynamic Flow Rate Control**:
     - Bio-Marlin introduces real-time extrusion adjustments using G-code commands:
       - **`M221 S[value]`**: Modify the extrusion flow rate, useful for fine-tuning bio-ink viscosity. Example: `M221 S110` sets a 10% increase in flow rate.
       - **`M900 K[value]`**: (Optional) Set custom viscosity control for different materials; add specific profiles for bio-inks and gels, enhancing material compatibility.

   - **Material-Specific Profiles**:
     - **Material Calibration Commands**: Custom commands like `M902` for low-viscosity materials and `M903` for high-viscosity hydrogels, allowing quick changes based on the material in use.
     - **Pressure and Speed Adjustments**: For pneumatic or motor-driven extrusion setups, control pressure or torque through G-code commands or add physical hardware adjustments if needed.

### 2. Bed Area and Travel Limits
   - **Defined Print Bed**: The bioprinter bed area is set to 8x8 cm by default. Adjustments to X and Y bed limits are defined in `Configuration.h`:
     - `#define X_BED_SIZE 80`
     - `#define Y_BED_SIZE 80`
   - **Soft Endstop Limits**: Enabling soft endstops helps maintain printing within this constrained area. Adjust these in **Configuration.h**:
     ```cpp
     #define MIN_SOFTWARE_ENDSTOPS
     #define MAX_SOFTWARE_ENDSTOPS
     ```

### 3. Temperature Control
   - **Cooling System for Hydrogels**:
     - The nozzle temperature controller in Bio-Marlin is modified to maintain low temperatures suitable for biocompatible materials like hydrogels. The maximum temperature is capped at 23°C to prevent denaturation or material degradation.
     - **G-code for Temperature Setting**:
       - Set desired cooling temperatures with `M104 S[temperature]`:
       ```gcode
       M104 S20 ; Set nozzle temperature to 20°C
       ```

### 4. Firmware Structure and File Organization
   - Bio-Marlin is organized to include only essential files:
     - **Configuration.h and Configuration_adv.h**: Central configuration files containing settings for bed size, temperature, extruder limits, and endstops.
     - **Reduced Display Menus**: Only displays critical information needed for operation, avoiding unnecessary interface clutter.
     - **No Heated Bed or Screen Files**: Unused elements like the heated bed and screen files are removed for simplicity.

### 5. Error and Safety Management
   - **Temperature Error Handling**: Integrated temperature failsafe to prevent exceeding 23°C, with automatic shutdown if temperatures rise above the threshold.
   - **Over-Extrusion Protection**: Automatic adjustments in extrusion feed rate to prevent clogging or over-extrusion based on viscosity settings.

---

## Installation and Configuration

### Prerequisites
- **Hardware Requirements**: Compatible 3D printer board with ( MKS , RAMPS )
- **Software Requirements**: [Arduino IDE](https://www.arduino.cc/en/software) for firmware flashing.

### Installation Steps
1. **Clone the Repository**:
   ```bash
   git clone https://github.com/yourusername/Bio-Marlin.git
   ```
2. **Modify Configuration Files**:
   - Open **Configuration.h** and **Configuration_adv.h** to adjust bed size, nozzle temperature, and extrusion parameters as needed.
3. **Upload Firmware**:
   - Connect your bioprinter and upload the firmware using the Arduino IDE.

### Calibration
1. **Set Bed and Extruder Settings**:
   - Fine-tune bed leveling and endstop positions based on the reduced 8x8 cm print area.
2. **Material Calibration**:
   - Test bio-ink or hydrogel extrusion by adjusting `M221` flow rates to suit material viscosity.
3. **Temperature Validation**:
   - Ensure the nozzle maintains the cooling temperature for bio-materials, testing for any anomalies.

---

## Known Issues and Troubleshooting
Bio-Marlin V1.2 is a beta firmware, and users may encounter issues during installation or use. Known issues include:
- **Extruder Stalling**: High-viscosity materials may cause temporary stalls in extrusion. Adjust `M221` for better control.
- **Temperature Overshoot**: For sensitive materials, monitor temperature closely to avoid exceeding 23°C.
- **G-code Incompatibilities**: Some Marlin-specific G-code commands may not function as intended in Bio-Marlin’s modified setup.

---

## Contributing
We welcome contributions to expand and refine Bio-Marlin’s capabilities. If you’d like to contribute:
1. Fork the repository.
2. Create a new branch for your feature or fix.
3. Submit a pull request with detailed comments on your updates.

---

## Future Development Goals
Bio-Marlin aims to expand bioprinting functionality further, with planned updates such as:
- **Enhanced Extrusion Control**: Support for variable pressure-based extrusion systems.
- **Material Profiles Library**: Predefined profiles for a wider range of bio-inks and hydrogels.
- **Improved Community Support**: Additional documentation, tutorials, and a user forum for troubleshooting and sharing techniques.

---

