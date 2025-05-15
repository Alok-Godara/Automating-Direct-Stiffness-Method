# Elastic Structural Analysis of Plane Frames Using the Direct Stiffness Method

## Overview  
This project implements a **Python-based structural analysis tool** for plane frames using the Direct Stiffness Method. It handles arbitrary geometries, support conditions (fixed, pinned, roller), and various loads (point, UDL, UVL). The code is verified against STAAD Pro results for accuracy[1][4].

---

## Features  
- **Input Flexibility**: Reads geometry and loads from `nodes.csv` and `members.csv`[1][6].  
- **Load Handling**: Supports point loads, UDL, UVL, and trapezoidal loads[2][4].  
- **Symbolic Computation**: Uses SymPy to solve equilibrium equations[2][4].  
- **Post-Processing**: Outputs displacements, reactions, and member end forces[1][4].  

---

## File Structure  
| File                   | Description                                  |
|------------------------|----------------------------------------------|
| `asa_project_final.py` | Main Python implementation                  |
| `ASA_Project_Final.ipynb` | Jupyter notebook with interactive testing  |
| `nodes.csv`            | Node coordinates, supports, and loads[6]    |
| `members.csv`          | Member connectivity and properties[5]      |
| `ASA_Project_Report.pdf` | Detailed theory and verification[4]        |

---

## Input Formats  

### `nodes.csv` Example  
node_id,support_type,x,y,external_H,external_V,external_M
1,fixed,0,0,0,0,0
2,free,8,5,0,0,0
3,fixed,12,5,0,0,0

### `members.csv` Example  
member_id,node1,node2,A,E,I,loads
1,1,2,0.01,2.05E+11,8.33E-06,"uniform_distributed_load;-30000;0,0"


---

## How It Works  
1. **Stiffness Matrix Assembly**:  
   - Computes local stiffness matrices for each member[2][4].  
   - Transforms to global coordinates using rotation matrices[2][4].  
   - Assembles global stiffness matrix \( [K] \)[4]:  
     \[
     \{F\} = [K]\{d\} + \{F_{FE}\} - \{F_{ext}\} - \{R\} = 0
     \]

2. **Load Processing**:  
   - Calculates fixed-end forces for distributed loads[2][4].  

3. **Solution**:  
   - Solves symbolic equations for displacements and reactions using SymPy[2][4].  

---

## Results  
| Variable                  | Value (mm/rad/kN) | STAAD Pro Equivalent[4] |
|---------------------------|-------------------|-------------------------|
| Horizontal_Displacement_2 | 0.0005877         | 357.297 mm              |
| Vertical_Reaction_1       | 251.361 kN        | 251.361 kN              |
| Moment_1                  | -249.067 kN·m     | -249.067 kN·m           |

---

## Usage  
1. Edit `nodes.csv` and `members.csv`.  
2. Run:  `python asa_project_final.py`.
3. Compare results with STAAD Pro output[4].  

---

## References  
- Full theoretical derivation: `ASA_Project_Report.pdf`[4]  
- Course guidelines: `CIL3060-Lab-Project.pdf`[1]  

**Authors**: Abhimanyu Bansal (B22CI001), Alok Godara (B22CI004)  
**License**: Academic use for CIL3060 course[1].  

  
