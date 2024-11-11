# Bio-Marlin V1.2 (Beta)

### Overview
**Bio-Marlin** is a customized version of the Marlin firmware (based on Marlin 1.1.9) tailored specifically for 3D bioprinting applications. This firmware is designed to streamline and enhance the bioprinting process by optimizing certain parameters and removing unnecessary components to focus on the specific requirements of biofabrication.

> **Note**: Bio-Marlin V1.2 is in a beta stage. This version is a work in progress and relies on community feedback and contributions to improve its functionality and stability.

---

### Key Features
- **Streamlined Design**:
  - **Removed Files**: Non-essential files, including language and screen files, have been removed to reduce firmware size and improve performance.
  - **No Heated Bed**: The heated bed feature has been disabled, as most bioprinting processes do not require it.

- **Bioprinting-Specific Enhancements**:
  - **Small Print Bed Size**: The print bed area has been optimized for bioprinting at 8x8 cm, suitable for small-scale biofabrication applications.
  - **Controlled Extruder Speed**: To manage the viscosity of bio-inks, extruder speed can be fine-tuned directly through G-code commands. Adjusting this parameter can help in handling different viscosities based on material properties.
  - **Temperature Control for Hydrogel Storage**: The nozzle temperature has been repurposed to store hydrogel during printing, with a maximum temperature setting of 23°C to maintain the integrity of temperature-sensitive bio-inks.

---

### License
Bio-Marlin is based on the original Marlin firmware and respects the terms of the Marlin license. This project does not resell or rebrand the original firmware; it is a modification aimed at benefiting the bioprinting community and advancing the science of biotechnology. All contributions are made in the spirit of open sharing and collaboration.

---

### Getting Started

1. **Clone the Repository**:
   ```bash
   git clone https://github.com/yourusername/Bio-Marlin.git
   ```
2. **Customize Configuration**:
   - Adjust bed size, nozzle temperature, and extrusion settings in **Configuration.h** as needed for your setup.

3. **Upload to Your 3D Printer**:
   - Flash the modified firmware to your 3D bioprinter, following Marlin’s upload instructions.

---

### Extruder Viscosity Control
To control viscosity, you can use specific G-code commands to adjust extruder parameters:
- **G-code Flow Rate Adjustment**:
  - Use `M221 S<value>` to control flow rate.
  - Example: `M221 S120` increases flow rate by 20% for thicker materials.

- **Custom Commands for Pressure and Speed Control**:
  - To fine-tune extrusion speed based on viscosity, custom G-codes like `M900` could be added for specific viscosity profiles. 

---

### Known Issues & Community Feedback
As Bio-Marlin is in beta, users may encounter some functionality issues. Please report issues and suggest improvements in the **Issues** section. Community contributions are encouraged to enhance and refine this firmware for a variety of bioprinting needs.

---

### Contributing
We welcome contributions to expand Bio-Marlin's capabilities. If you’d like to contribute:
1. Fork the repository.
2. Make your changes.
3. Submit a pull request with a detailed description.

---

### Future Directions
Planned features include:
- Enhanced control over bio-ink pressure and extrusion for different bio-materials.
- Expanded G-code command library for bioprinting functions.
- Improved stability and compatibility across different hardware.

--- 

