# 🎮 Input System & VR Setup Guide

This document explains the input handling system configuration and how to set up VR controls for Meta Quest 2.

---

## 📋 Input System Configuration

### Current Setup
This project uses Unity's **New Input System** (Input System Package) for handling all input, including:
- Traditional controllers (steering wheels, gamepads)
- VR controllers (Meta Quest 2 Touch controllers)
- XR Interaction Toolkit integration

### Project Settings
- **Active Input Handler**: Input System Package (New) ✅
- **Old Input Manager**: Disabled ❌
- **Input System Package Version**: 1.11.2

### Why Use the New Input System?

The new Input System provides:
1. **Better VR Support**: Seamless integration with XR Interaction Toolkit
2. **Action-based Input**: More flexible and easier to configure
3. **Multi-device Support**: Handle multiple controllers simultaneously
4. **Modern Unity Standard**: Recommended by Unity for all new projects

---

## ⚠️ StandaloneInputModule Warning - RESOLVED

### The Issue
Previously, the EventSystem was using `StandaloneInputModule`, which is designed for the old Input Manager. This caused the following warning:

> "You are using StandaloneInputModule, which uses the old InputManager. You are using the new InputSystem, and have the old InputManager disabled. StandaloneInputModule will not work."

### The Solution ✅
The project has been updated to use `InputSystemUIInputModule` in both main scenes:
- **SUV.unity**: EventSystem now uses InputSystemUIInputModule
- **Sports Car.unity**: EventSystem now uses InputSystemUIInputModule

This component is compatible with the new Input System and works correctly with VR and traditional input devices.

---

## 🥽 Meta Quest 2 VR Setup

### Prerequisites
1. **Unity Version**: 2022.3.51f1 or higher
2. **Required Packages** (already installed):
   - XR Interaction Toolkit (2.6.3)
   - OpenXR (1.13.2)
   - Oculus XR Plugin (4.3.0)
   - Input System (1.11.2)

### Project Configuration

#### 1. XR Plug-in Management
Go to **Edit → Project Settings → XR Plug-in Management**:
- ✅ Enable **OpenXR**
- ✅ Select **Oculus** as OpenXR runtime
- ✅ Ensure **Meta Quest Support** is enabled

#### 2. OpenXR Settings
Go to **Edit → Project Settings → XR Plug-in Management → OpenXR**:
- Add **Interaction Profiles**:
  - Oculus Touch Controller Profile
  - Meta Quest Touch Pro Controller Profile (if available)
- Enable **Meta Quest Feature** under Features

#### 3. Player Settings
Go to **Edit → Project Settings → Player → Other Settings**:
- **Color Space**: Linear ✅
- **Rendering Path**: Forward ✅
- **Stereo Rendering Mode**: Single Pass Instanced ✅

### Meta Quest 2 Controller Mapping

The XR Interaction Toolkit provides default bindings for Meta Quest 2 controllers:

| Controller Action | Meta Quest 2 Binding |
|------------------|----------------------|
| **Grip** | Grip Button (both hands) |
| **Trigger** | Index Trigger (both hands) |
| **Primary Button** | A Button (right), X Button (left) |
| **Secondary Button** | B Button (right), Y Button (left) |
| **Thumbstick** | Thumbstick (both hands) |
| **Menu** | Menu Button (left) |
| **Tracking** | Automatic 6DOF tracking |

### Setting Up Custom VR Controls

If you want to customize VR controls for your car simulation:

#### Option 1: Using XR Interaction Toolkit (Recommended)
1. Add **XR Origin** to your scene (already present in this project)
2. Configure **XR Ray Interactor** for pointing interactions
3. Use **XR Direct Interactor** for grabbing interactions
4. Bind actions in the **XR Interaction Manager**

#### Option 2: Using Input Actions
1. Create a new **Input Actions Asset**:
   - Right-click in Project → Create → Input Actions
2. Define actions for your VR controls:
   - Accelerate (Right Trigger)
   - Brake (Left Trigger)
   - Steering (Right Thumbstick)
3. Reference the Input Actions in your `InputSystemUIInputModule`

### Example: Configuring VR Steering

```csharp
// Example script snippet for VR steering with Meta Quest 2
using UnityEngine;
using UnityEngine.InputSystem;

public class VRCarController : MonoBehaviour
{
    [SerializeField] private InputActionReference steeringAction;
    [SerializeField] private InputActionReference accelerateAction;
    [SerializeField] private InputActionReference brakeAction;
    
    void Update()
    {
        float steering = steeringAction.action.ReadValue<Vector2>().x;
        float accelerate = accelerateAction.action.ReadValue<float>();
        float brake = brakeAction.action.ReadValue<float>();
        
        // Apply to car controller
        // ... your car control logic here
    }
}
```

---

## 🎯 Current Control Schemes

### 1. NITTO Drive 1 Pro Steering Wheel (Xbox Mode)
See [README.md](README.md) for detailed button mapping.

### 2. Meta Quest 2 VR Controllers
The project supports VR head tracking for immersive driving. For full VR controller integration:
- Use the XR Interaction Toolkit components
- Configure custom Input Actions as shown above
- Bind VR controller inputs to car controls in your scripts

### 3. Generic Controllers
The Input System supports any controller recognized by Unity. To add support:
1. Ensure the controller is detected in **Edit → Project Settings → Input System Package**
2. Create or modify Input Actions to include the new controller
3. Test in Play Mode with the controller connected

---

## 🔧 Troubleshooting

### "Input System Package (New) is not installed"
- Go to **Window → Package Manager**
- Search for "Input System"
- Install/Update to latest version (currently 1.11.2)

### VR Controllers Not Responding
1. Check **XR Plug-in Management** settings
2. Verify **OpenXR** is enabled with **Meta Quest Support**
3. Ensure your Meta Quest 2 is connected via:
   - Oculus Link (wired)
   - Air Link (wireless)
4. Restart Unity Editor after changing XR settings

### EventSystem Warnings
If you see warnings about StandaloneInputModule:
- The EventSystem should use `InputSystemUIInputModule`
- This has been configured in SUV.unity and Sports Car.unity
- For new scenes, add EventSystem with InputSystemUIInputModule

### Input Not Working in Build
1. Ensure **Active Input Handler** is set to "Input System Package (New)"
2. Include all required Input Actions in your build
3. Check that XR plugins are included in the build settings

---

## 📚 Additional Resources

- [Unity Input System Documentation](https://docs.unity3d.com/Packages/com.unity.inputsystem@1.11/manual/index.html)
- [XR Interaction Toolkit Documentation](https://docs.unity3d.com/Packages/com.unity.xr.interaction.toolkit@2.6/manual/index.html)
- [Meta Quest Development Guide](https://developer.oculus.com/documentation/unity/)
- [OpenXR Documentation](https://docs.unity3d.com/Packages/com.unity.xr.openxr@1.13/manual/index.html)

---

## ✅ Summary

**Input System Status**: ✅ Fully Configured
- New Input System is active
- StandaloneInputModule replaced with InputSystemUIInputModule
- VR-ready with XR Interaction Toolkit support

**Next Steps for VR Development**:
1. Create custom Input Actions for Meta Quest 2 controls
2. Bind VR controller inputs to car controls
3. Test in VR with Meta Quest 2 connected
4. Iterate and refine the VR driving experience

For questions or issues, please open a GitHub issue or contact the project maintainers.
