# Pure Pursuit Path Tracking in C++

This project implements the **Pure Pursuit** algorithm for path tracking using C++ and simulates the movement of a vehicle on a predefined trajectory. The project demonstrates the use of a Pure Pursuit controller along with a PID controller for velocity adjustment. The path data is loaded from a file, and the vehicle's position is plotted in real-time using **matplotlibcpp**. 

## Features

- **Pure Pursuit Algorithm**: Used for steering control to follow a path.
- **PID Controller**: Helps in maintaining the vehicle's velocity to match the target speed.
- **Path Data**: The trajectory points are stored in a `points.txt` file, which can be modified for different paths.
- **Visualization**: The real-time position of the vehicle and its trajectory are visualized using `matplotlibcpp`.

## Project Structure

- **pure\_pursuit.cpp**: The main program which runs the simulation, loads path data, and visualizes the vehicle's movement.
- **pure\_pursuit\_controller.cpp**: Contains the implementation of the PID controller, vehicle kinematics, and the Pure Pursuit controller logic.

## Requirements

To run this project, you'll need the following dependencies:

- **C++ Compiler** **(GCC or Clang)**
- **Boost Library**: For `boost::circular_buffer` and file handling.
- **matplotlibcpp**: A C++ interface to Python’s `matplotlib` for plotting (visualization).


## Usage

The program loads a list of trajectory points from the `points.txt` file. Each line in this file should contain an `x` and `y` coordinate representing a point on the path (in meters). For example:

```
0.0 -20.0
1.0 -18.0
2.0 -16.0
...
```

Make sure to adjust the path in the code (`filePath`) to match the location of your `points.txt` file.

### Parameters

- **PID Controller Parameters**:

  - `kP`, `kI`, `kD`: Proportional, Integral, and Derivative gains.

- **Pure Pursuit Parameters**:

  - `klD`: Look Ahead Distance Gain.
  - `lD`: Look Ahead Distance.

- **Vehicle Parameters**:

  - `x`, `y`: Initial position of the vehicle.
  - `yaw`: Initial orientation (in radians).
  - `vel`: Initial speed of the vehicle.
  - `maxSpeed`: Maximum speed the vehicle can reach.

- **Goal Pose**:

  - The goal pose (`goalPose`) is the target position the vehicle aims to reach.

## Visualization

During the simulation, the path and vehicle's position are plotted in real-time. You can adjust the plotting interval and other visual settings as needed. 

## Example Output

- The vehicle will start at the initial position `(0, -20)` and attempt to follow the path points loaded from `points.txt`.
- The simulation will stop when the vehicle reaches the goal position or after the defined time limit (`maxTime`).

## Future Improvements

- **Path Planning**: Integrate more advanced path planning algorithms to generate the trajectory dynamically.
- **Obstacle Avoidance**: Add obstacle detection and avoidance to make the path-following more realistic.
- **More Vehicle Models**: Implement more vehicle types (e.g., Ackermann steering) and compare the performance.


