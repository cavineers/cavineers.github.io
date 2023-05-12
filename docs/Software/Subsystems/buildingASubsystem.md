## Upgrading your enviornment

Before you can start coding the robot, you'll need to install one more thing, [WPILib](https://docs.wpilib.org/en/stable/docs/zero-to-robot/step-2/wpilib-setup.html). This is the library we use when programming the installation includes the libraries and tools needed to program and deploy code to the robot.

Additionally, you'll need to make sure your VSCode has the updated extensions. To do this, go to the extensions tab and search for WPILib and install the WPILib extension.

## Creating your subsystem

To create a subsystem in Java, you use the `class` keyword followed by the name of the manipulator you are making a subsystem for and lastly the subsystem class must extend SubsystemBase. Here's an example:

```java
public class Shooter extends SubsystemBase {
    
}
```

In this example, we have created a class called `Shooter` in order to create a subsystem for a shooter. For the remainder of creating this subsystem, or in this example, shooter all code will lie within this class. 

## The periodic function

All subsystems have a periodic function:

```java
public class Shooter extends SubsystemBase {

    public void periodic() {

    }
}
```

A periodic function is a function that is designed to perform a specific task or set of tasks in a subsystem. This function is ran at a constant interval (about every 20 milliseconds) and can be used for: Constantly checking a value like a sensor value, projecting a value onto smart dashboard, etc.

```java
public class Shooter extends SubsystemBase {

    public void periodic() {

        if (getSensor() == true) {
            System.out.println("Sensor pushed!")
        }
    }
}
```

In this example, when the sensor is pushed it prints "Sensor pushed!".

