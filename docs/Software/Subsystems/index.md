# Subsystems

A mechanical subsystem is a specific part of the robot that will serve a special function. For example, the drivetrain is the subsystem on the robot that serves to drive the robot around the field. Each year the subsystems will change, but the general idea of a subsystem will remain the same.

In programming, a subsystem is a file that will hold the bulk of the code that is for a single mechanical subsystem. These subsystem files house the declaration of motors and sensors, as well as the methods that will be used to control the subsystem. The subsystem files are then declared in the robot container file, where the subsystems are instantiated and used.

These are the subsystems from the 2022 Charged UP Robot, Kelvin: ![Alt text](../../assets/subsystems.png)

## Why do we use subsystems?

By dividing the robot into different subsystems, we are able to work on different parts of the robot at the same time. For example, one person can work on the drivetrain while another person works on the shooter. Additionally, by organizing the code into separate subsystems, it becomes easier to manage and debug the code, as well as to make changes or upgrades to specific subsystems without affecting the rest of the robot's functionality. By organizing our robot into subsystems, we can also reuse, as similar subsystems from different years can be adapted for use in new designs.