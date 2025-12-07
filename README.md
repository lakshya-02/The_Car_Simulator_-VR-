# 🚗 The Car Driving Simulator VR
A fully immersive car driving simulator in Unity with VR support using Meta Quest 2 and NITTO Drive 1 Pro steering wheel. The simulator features realistic car physics, VR head tracking, and controller-based driving mechanics.  

---

## 🔥 Features  
✅ **Realistic Driving Physics:**  
- Smooth acceleration, braking, and steering.  
- Natural vehicle movement with proper gravity and wheel colliders.  

✅ **VR Integration:**  
- Supports Meta Quest 2 with OpenXR.  
- first-person driver view.  

✅ **Steering Wheel Controls:**  
- NITTO Drive 1 Pro compatibility with Xbox mode.  
- Accurate steering, acceleration, braking, and reverse control.  

✅ **Camera System:**  
- VR camera rig follows the car with realistic driver perspective.  
- Multiple views: Driver view, hood view, and free-look.  

✅ **Optimized Performance:**  
- Uses Single-Pass Rendering for better VR performance.  
- Stable car physics to prevent flipping.
      
✅ **NO Need For any Special item:**
- You Can Play this Game Via any controller
- No need For VR (VR is for Better experince ) to Play
---

## 🛠️ Tech Stack & Tools  
- **Game Engine:** Unity 2022.3.51f1  
- **VR SDK:** OpenXR with Meta Quest 2 support  
- **Input System:** Unity Input System Package (New) 1.11.2 + XR Interaction Toolkit  
  - See [INPUT_SETUP.md](INPUT_SETUP.md) for detailed input configuration
- **Hardware:**  
    - Meta Quest 2 VR headset  
    - NITTO Drive 1 Pro steering wheel (Xbox mode)  
- **Assets:**  
    - Vehicle Physics Pro (VPP) → For realistic car behavior   
    - XR plugins for Meta Quest 2  

---

## 🔧 Installation & Setup  

✅ **1. Clone the Repository**  
```bash
git clone https://github.com/lakshya-02/The_Car_Simulator_-VR-  
cd VR-Game  
```

✅ **2. Unity Configuration**  
- Open the project in **Unity 2022.3.34f1** or higher.  
- Go to **Edit → Project Settings → XR Plug-in Management:**  
    - Enable **OpenXR**.  
    - Select **Meta Quest Support**.  

- **Player Settings:**  
    - Go to **Edit → Project Settings → Player → Other Settings**.  
    - Set **Color Space** to Linear.  
    - Set **Rendering Path** to Forward.  
    - Check **Single-Pass Instanced Rendering**.  

- **Enable VR Preview:**  
    - Go to **Oculus App → Devices → Air Link → Pair with Unity**.  
    - Ensure **Oculus Link** is enabled.  

---

## 🎮 Steering Wheel Controls  

| Button                | Action               | Unity Input Name       |
|-----------------------|----------------------|------------------------|
| **Steering**          | Left / Right Turn    | `Steering Axis`        |
| **White Button (Right)**| Brake                | `joystick button 4`    |
| **White Button (Left)**| Accelerate           | `joystick button 5`    |
| **Metal LB**           | Respawn the Car      | `joystick button 6`    |
| **Metal RB**           | Change Toggle/View   | `joystick button 7`    |
| **X Button**           | Reverse Gear         | `joystick button 2`    |
| **Y Button**           | Neutral Gear         | `joystick button 3`    |
| **B Button**           | Increase Gear        | `joystick button 1`    |
| **A Button**           | Turn On Engine       | `joystick button 0`    |


✅ **VR Controls**  
- **Head Tracking:**  
    - Move your head to look around inside the car.  
- **Car Movement:**  
    - Use the steering wheel for left and right movement.  
    - Accelerate, brake, and reverse using the pedal system.  
- **Reset View:**  
    - Click the right joystick to re-center the VR view.  

---

## 📸 Screenshots  
![Screenshot 2025-03-20 231432](https://github.com/user-attachments/assets/a6bb7066-f7e9-47e3-bae2-358099bb083f)
![Screenshot 2025-03-20 231945](https://github.com/user-attachments/assets/0a5b1d08-f7a1-44d7-9a58-4c653a2fdb89)
![Screenshot 2025-03-20 231834](https://github.com/user-attachments/assets/795340c2-4fe1-4d68-827b-8310266b09cc)
![Screenshot 2025-03-20 231758](https://github.com/user-attachments/assets/12cbd757-621d-4910-a005-29dab9dd3219)
![Screenshot 2025-03-20 231543](https://github.com/user-attachments/assets/a85ffbd8-c5bd-4bcf-a887-f5966e6e84eb)
---

## 🚀 How to Play  
1. Start Unity with your **Meta Quest 2** connected via **Air Link**.  
2. Press **Play** in Unity.  
3. Put on the **Meta Quest 2** headset.  
4. Use the steering wheel for driving and VR headset for a realastic view.  
5. Enjoy the immersive driving experience! 🚗🕶️  

---

## ⚙️ Customization  

✅ **Changing the Car Model:**  
- Go to **Assets → Prefabs → Car** → Replace the model with your custom car.  
- Ensure the wheel colliders and rigid body parameters are properly configured.  

✅ **Adjusting VR Camera Position:**  
- Move the **XR Origin** object in the hierarchy to adjust the camera height and position.  

✅ **Modifying Car Physics:**  
- Open the **CarController** script → Adjust values like:  
    - `steeringSpeed`, `maxSpeed`, and `acceleration`.  

✅ **Change Steering Sensitivity:**  
- Modify the sensitivity in **Input Actions** for smoother steering.  

---

## 🛠️ Troubleshooting  

✅ **Input System Warnings:**  
- The project uses Unity's **New Input System** (not the old Input Manager).
- See [INPUT_SETUP.md](INPUT_SETUP.md) for detailed configuration guide.
- If you see StandaloneInputModule warnings, they have been resolved in the latest version.

✅ **VR Not Detecting in Unity:**  
- Ensure **Air Link** is enabled in Meta Quest 2 settings.  
- Restart Unity if VR is not detected.  

✅ **Steering Wheel Not Recognized:**  
- Set the **NITTO Drive 1 Pro** to Xbox Mode.  
- Restart Unity after switching controller modes.  

✅ **Laggy Performance:**  
- Lower the **Fixed Timestep** to `0.01` in **Project Settings → Time**.  
- Reduce shadow quality and enable **Single-Pass Rendering**.  

---

## 🛠️ Future Enhancements  
🔥 **Multiplayer Mode:** Drive with friends in VR multiplayer mode.  
🔥 **Weather Effects:** Realistic rain, fog, and snow effects.  
🔥 **Day-Night Cycle:** Dynamic lighting conditions.  
🔥 **Custom Cars:** Add new car models with unique physics.  

---

## 💻 Contributing  

1. Fork the repository.  
2. Create a new branch:  
```bash
git checkout -b feature/your-feature-name  
```  
3. Commit your changes:  
```bash
git commit -m "Add new feature"  
```  
4. Push the branch:  
```bash
git push origin feature/your-feature-name  
```  
5. Submit a **Pull Request**.  

---

## 📄 License  
This project is licensed under the **MIT License**. You are free to use and modify but give proper Credit. 

---

## 🎯 Credits  
- **Unity Asset Store Assets** → Vechile Physics Pack   
- **Meta Quest 2** → For VR integration.  
- **NITTO Drive 1 Pro** → For steering wheel controls.  

---

## 🚀 Contact  
For any issues or suggestions:  
📧 Email: lakshyasingh@gmail.com   
📌 GitHub: https://github.com/lakshya-02    
📌 GitHub: https://github.com/Tahaa-Mushtaq      
📌 LinkedIn: https://www.linkedin.com/in/lakshya-singh-2833a2328/    
---
