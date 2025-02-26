# Real-time Metahuman Setup using ThreeDPoseTracker, VMC Protocol, MOP Protocol, and Mop Plugin for Unreal Engine 5.5

## **Workflow Overview**
This guide outlines the workflow for setting up a real-time metahuman rig using various protocols and plugins.

Key protocols::

- **Virtual Motion Capture (VMC) Protocol:** A system developed to facilitate communication between motion capture software and applications like Unity, enabling the animation of VRM avatars. 

- **Motion Over Protocol (MOP):** A communication protocol used for utility services such as uploading and downloading system software, remote testing, and problem diagnosis. 

### **Workflow Steps:**
1. **ThreeDPoseTracker (TDPT)** → Enable VMC server in TDPT
2. **Start VMCtoMOP** → Convert VMC protocol data to MOP protocol
3. **Mop4UE** → Integrate MOP protocol with Unreal Engine

## **Dependencies Downloads**
Download and install the required software:

- **ThreeDPoseTracker for Windows v0.5.1**  
  [Download Here](https://booth.pm/ja/items/3698596)
  
- **VMC to MOP**  
  [Download Here](https://github.com/HAL9HARUKU/VMCtoMOP/releases)
  
- **MopUE5 Plugin (Supports UE5.3)**  
  Clone from GitHub: [MopUE5.3 Repository](https://github.com/cbb2625274797/MopUE5.3)

---

## **Setting Up the Unreal Engine Project**

1. **Create a New Unreal Engine 5 Project**
2. **Install the Required Plugin:**
   - Navigate to **Edit** → **Plugins**
   - Enable **OSC (Open Sound Control)**
3. **Close the Project**
4. **Manually Add the MopUE5 Plugin:**
   - Navigate to the project directory
   - Create a new folder named **Plugins**
   - Extract the MopUE5 plugin into this folder (should be named `mop`)

---

## **Starting the Rigging Programs**

1. **Launch ThreeDPoseTracker**
   - Run: `ThreeDPoseTracker_Win_x64_v0_5_1/ThreeDPoseTracker.exe`
   - Go to **Configuration** → **Others**
     - Enable **"Send VMC Protocol"**, and note the port number

2. **Launch VMCtoMOP**
   - Run: `VMCtoMOP/VMCtoMOP.exe`
   - Set the **Receive Port** to match the port from TDPT (if needed)
   - Note the **Send Port**

---

## **Reopening the Unreal Project**

- Relaunch the Unreal Engine 5 project
- Agree to any prompts regarding the version difference (originally designed for UE5.3 but works fine with UE5.5)

---

## **Adding a Live Rigged Metahuman**

### **Setting Up the Metahuman Character**
1. Add a Metahuman character to the scene
2. Open the placed Metahuman by **Right-click → Edit**
3. **Modify Class Defaults:**
   - Under **Class Defaults**:
     - **Select "Body"** on the left-hand side
     - **Set Animation Mode:** "Use Animation Blueprint"
     - **Set Animation Class:** "ABP_MetaHuman_Rotation"
   - Under **Class Settings:**
     - **Set Parent Class:** "BP Mop Pawn"

### **Enabling Plugin Content in Content Browser**
- Open the **Content Browser**
- Click on **Settings (top-right corner)**
- Enable **"Show Plugin Content"**

### **Adding the MOP Receiver**
1. Navigate to `Plugins/Mop Contents/Blueprints`
2. Add **BP_Mop_Receiver** somewhere in the world

### **Configuring the Metahuman Object**
1. Open the Metahuman object's **Details** panel
2. Navigate to the **Mop Section**
   - Set **Mop_Receiver** to **BP_MopReceiver**

### **Configuring the BP_MopReceiver Object**
1. Open `BP_MopReceiver` object properties
2. Navigate to the **Mop Section**
   - Set the **Port** to match the port from VMCtoMOP

---

## **Final Step: Running the Live Rigged Character**
Once all steps are complete, launch the project and enjoy your real-time rigged Metahuman!

