# Robotic Parallel-Jaw Industrial Gripper Design

![CAD View](docs/assembly.jpeg)

A parametric CAD design and static structural validation of a two-finger parallel-jaw industrial gripper utilizing a rack-and-pinion actuation mechanism. Designed in **Autodesk Fusion 360** and validated for an **8 kg payload capacity**.

---

## 🛠️ Design & Key Specifications

| Parameter | Specification / Value |
| :--- | :--- |
| **Payload Capacity** | $8\text{ kg}$ ($78.48\text{ N}$) |
| **Actuation Mechanism** | Central Pinion driving opposing Rack Jaws |
| **Servo Actuator** | DS5160 SSG Digital Metal-Gear Servo |
| **Maximum Jaw Opening** | $72\text{ mm}$ ($36\text{ mm}$ travel per jaw) |
| **Pinion Parameters** | 20 Teeth, Module 1, Pitch $\varnothing 20\text{ mm}$, $10\text{ mm}$ Thickness |
| **Guide Rods** | Dual $3\text{ mm}$ diameter $\times 130\text{ mm}$ Steel Rods |
| **Structural Material** | Aluminium 6061-T6 (Base, Jaws, Pinion Holder, Arm Connection) |
| **Drive Components** | Steel (Pinion, Coupler, Guide Rods) |
| **Contact Surface** | Butyl Rubber Jaw Pads |

---

## 📊 Static Structural Simulation (FEA Summary)

Static stress analysis was conducted in **Autodesk Fusion 360** (Static Stress Study) to evaluate structural integrity under full gripping load.

* **Applied Load:** $120\text{ N}$ per jaw (opposing gripping force derived for an 8 kg payload at $\mu = 0.5$, $SF = 1.5$)
* **Boundary Condition:** Fixed constraint at the robotic arm interface + standard gravity ($9.807\text{ m/s}^2$)
* **Mesh Statistics:** 526,544 Nodes | 332,937 Parabolic Solid Elements

### FEA Results

| Metric | Simulated Result | Target / Yield Strength | Status |
| :--- | :--- | :--- | :--- |
| **Minimum Safety Factor** | **11.98** | $\ge 1.5$ | Pass (Very Strong) |
| **Max Von Mises Stress** | **17.279 MPa** | $369\text{ MPa}$ (Al 6061-T6) / $207\text{ MPa}$ (Steel) | Pass |
| **Max Displacement** | **0.003 mm** | Negligible deflection at jaw tips | Pass |
| **Max Equivalent Strain** | $1.568 \times 10^{-4}$ | Within elastic limit | Pass |

---

## 🧰 Bill of Materials (BOM) & Component List

| Item | Component Name | Qty | Material | Description |
| :---: | :--- | :---: | :--- | :--- |
| 1 | `gripper_base` | 1 | Aluminium 6061-T6 | Main structural enclosure |
| 2 | `jaw:1` & `jaw 2:1` | 2 | Aluminium 6061-T6 | Combined rack and jaw bodies |
| 3 | `pinion` | 1 | Steel | 20-tooth, module-1 spur gear |
| 4 | `pinion_holder` | 1 | Aluminium 6061-T6 | Bearing support for pinion shaft |
| 5 | `rod:1` & `rod 2:1` | 2 | Steel | $3\text{ mm} \times 130\text{ mm}$ linear guide rods |
| 6 | `coupler` | 1 | Steel | $6\text{ mm}$ shaft coupler to servo |
| 7 | `DS Servo DS5160 SSG` | 1 | Standard Hardware | Digital metal-gear servo actuator |
| 8 | `jaw_pad:1` & `jaw_pad (1):1`| 2 | Butyl Rubber | High-friction jaw contact pads |
| 9 | `arm_connection` | 1 | Aluminium 6061-T6 | Robotic arm flange mounting plate |
| 10| Fasteners | Misc | Steel / Aluminium | M4x20 & M5x08 Socket Head Screws |

---

## 🔧 Assembly Instructions

Follow these step-by-step instructions to assemble the physical/CAD gripper:

### Step 1: Base & Actuator Sub-Assembly
1. Mount the **DS5160 SSG Servo** onto the bottom opening of the `gripper_base`.
2. Secure the `arm_connection` plate to the base using M5 screws.
3. Attach the `coupler` onto the $6\text{ mm}$ output shaft of the servo motor and tighten the set screws.

### Step 2: Drive Mechanism & Pinion Integration
1. Press the `pinion` shaft ($6\text{ mm}$ bore) into the `coupler`.
2. Position the `pinion_holder` over the pinion shaft and secure it to the base. This isolates radial forces from the servo output shaft.

### Step 3: Guide Rods & Parallel Jaws Installation
1. Insert the two $3\text{ mm} \times 130\text{ mm}$ steel `rod` units horizontally through the guide holes in the `gripper_base`.
2. Slide `jaw:1` and `jaw 2:1` (rack assemblies) onto opposite ends of the guide rods.
3. Align both rack teeth simultaneously with opposite sides of the central `pinion` gear so that the jaws remain centered when closing.

### Step 4: Final Accessories & Verification
1. Mount the two `jaw_pad` rubber inserts onto the inner gripping faces of `jaw:1` and `jaw 2:1`.
2. Secure all structural side plates and screws (`screws`).
3. **Manual Check:** Rotate the pinion shaft manually; verify that both jaws open and close symmetrically through the $72\text{ mm}$ range without binding.

---

## 📂 Repository Structure

```text
├── CAD/
│   ├── gripper_assembly.f3d       # Autodesk Fusion 360 Master Model
│   └── STEP/                      # Exported STEP files for 3D printing/machining
├── FEA/
│   └── Simulation_Report.html     # Fusion 360 Static Stress Study Report
├── docs/
│   ├── engineering_report.pdf     # Detailed project & calculation report
│   └── images/                    # Assembly diagrams and stress maps
└── README.md
