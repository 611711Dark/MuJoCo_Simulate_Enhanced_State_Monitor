# MuJoCo Simulate Enhanced - Real-time State Monitor

[English](#english) | [中文](README_cn.md)

---

## English

### Overview

This project enhances the official MuJoCo `simulate` application by adding a comprehensive **Real-time State Monitor** that displays all joint positions (qpos) and velocities (qvel) in real-time during simulation.

### Features

- **📊 Complete State Monitoring**: Display all joint qpos and qvel data in real-time
- **🎯 Hierarchical Organization**: Clear grouping by joint name with separate qpos/qvel sections
- **⚡ Real-time Updates**: Values update automatically during simulation
- **💾 Compact Display**: Optimized format to maximize information density
- **🔧 Easy Integration**: Drop-in replacement for standard MuJoCo simulate

### What's New

#### Added Functionality
- **State (qpos/qvel) Section**: New collapsible UI section in the right panel
- **Joint-based Organization**: Each joint gets its own `jointname_qpos` and `jointname_qvel` subsections
- **Compressed Format**: Displays as `index:descriptor,value` (e.g., `0:qw,0.956`)
- **Smart Descriptors**: Shortened names (`ang` for angle, `av` for angular velocity, etc.)
- **Performance Optimized**: Updates only when section is expanded

#### Technical Implementation
- **Dynamic UI Generation**: Automatically creates UI elements based on model joints
- **Real-time Data Binding**: Direct access to MuJoCo's qpos/qvel arrays
- **Efficient Updates**: 60fps update rate with minimal performance impact
- **Memory Safe**: Proper bounds checking and memory management

### Usage

1. **Compile**: Use the modified `simulate.cc` and `simulate.h` files with your MuJoCo build
2. **Run**: Launch simulate as usual: `./simulate model.xml`
3. **Monitor**: Expand the "State (qpos/qvel)" section in the right panel
4. **Observe**: Watch real-time joint state changes during simulation

### Display Format

```
State (qpos/qvel)
├── root_qpos
│   ├── 0:qw,0.956     # Quaternion w component
│   ├── 1:qx,-0.000    # Quaternion x component
│   ├── 2:qy,0.260     # Quaternion y component
│   ├── 3:qz,0.000     # Quaternion z component
│   ├── 4:px,0.000     # Position x
│   ├── 5:py,0.000     # Position y
│   └── 6:pz,0.000     # Position z
├── root_qvel
│   ├── 0:avx,0.123    # Angular velocity x
│   ├── 1:avy,-0.045   # Angular velocity y
│   ├── 2:avz,0.000    # Angular velocity z
│   ├── 3:vx,0.000     # Linear velocity x
│   ├── 4:vy,0.000     # Linear velocity y
│   └── 5:vz,0.000     # Linear velocity z
├── joint_name_qpos
│   └── 7:ang,0.123    # Joint angle
├── joint_name_qvel
│   └── 6:av,0.045     # Joint angular velocity
```

### Supported Joint Types

- **Free Joints**: Full 6DOF with quaternion orientation
- **Ball Joints**: 3DOF rotational joints
- **Hinge Joints**: 1DOF rotational joints  
- **Slide Joints**: 1DOF translational joints

### Files Modified

- `simulate.cc`: Core implementation with state monitoring functions
- `simulate.h`: Header additions for state tracking data structures

### Compatibility

- **MuJoCo Version**: 3.3.4+
- **Platform**: Cross-platform (Windows, Linux, macOS)
- **Models**: Compatible with all MuJoCo model formats


### Installation Instructions

1.  Download `simulate.cc` and `simulate.h` files.
2.  Replace the corresponding files in the MuJoCo source code.
3.  Recompile the MuJoCo simulate application.
4.  Enjoy enhanced state monitoring!

### Contribution

Feel free to submit Issues and Pull Requests to improve this project.

---

**Note**: This enhanced version was developed and tested based on MuJoCo 3.3.4. For other versions, appropriate adjustments may be required.

