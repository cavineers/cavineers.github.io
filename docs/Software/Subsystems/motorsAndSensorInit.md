## Motors and sensors in a subsystem

In the following example subsystem we will be programming a simple subsystem that contains two motors and one limit switch sensor. This example subsystem will be called shooter but when making a subsystem it should describe what task the group of motors work together to accomplish.

## Initialization of subsystem motors

As stated we will be creating an example subsystem with two motors. The initializiation of the motors will lie within the subsystem class. In this example there will be one motor for the angle of the shooter and one motor for the speed of the shooter. Again this is just an example.

```java
public class Shooter extends SubsystemBase {
    
    public CANSparkMax shooterAngleMotor = new CANSparkMax(1, MotorType.kBrushless);
    public CANSparkMax shooterSpeedMotor = new CANSparkMax(2, MotorType.kBrushless);
}
```

These lines of code create new instances of the CANSparkMax class to control specific motors identified by their ID (1 and 2) and assigns them to the shooterAngleMotor and shooterSpeedMotor variables for further use in the program. The motor name should be a brief explanation of what the motor does. This motor initialization should be written the desired subsystem class the motor will be used for.

## Initialization of subsystem sensors

All subsystems have a periodic function:

```java
public class Shooter extends SubsystemBase {

    public CANSparkMax shooterAngleMotor = new CANSparkMax(1, MotorType.kBrushless);
    public CANSparkMax shooterSpeedMotor = new CANSparkMax(2, MotorType.kBrushless);

    private DigitalInput shooterButton = new DigitalInput(1);
}
```

This line creates a new instance of the DigitalInput class and asigns it to the variable buttonSensor and should be physically plugged into port one on the roborio. The Sensor name should be a brief explanation of what the sensor detects.

## Subsystem function

The subsystem function takes the same name as the subsystem class and can be used to set sparkMax functions. A sparkMax is the brain of the motor.

```java
public Shooter() {

    this.shooterAngleMotor.setIdleMode(IdleMode.kBrake);
    this.shooterSpeedMotor.setIdleMode(IdleMode.kBrake);

    this.shooterAngleMotor.setInverted(true);
    this.shooterSpeedMotor.setInverted(false);

    this.shooterAngleMotor.setSmartCurrentLimit(50);
    this.shooterSpeedMotor.setSmartCurrentLimit(75);
    }
```

In this example both motor's idle modes are set to brake. This makes the motors enter break mode when they are not moving. There are many other idle modes to choose from. This function also inverts shooterAngleMotor, which makes it spin the opposite way, and it sets the current limit on the angle motor to 50 and the speed motor to 75.