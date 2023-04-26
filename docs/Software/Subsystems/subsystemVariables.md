## Subsystem variables

We will be creating variables tell us what the speed of our motors are, their positions, etc.

## Motor speed variables

```java
    public CANSparkMax getShooterAngleMotor() {
        return this.shooterAngleMotor;
    }
    public CANSparkMax getShooterSpeedMotor() {
        return this.shooterSpeedMotor;
    }
```

These variables represent the speed of the motor and for example can be maniuplated with the line

```java
    getShooterAngleMotor().set(0.0);
```

This sets the speed of the shooterAngleMotor to zero or stationary

## Motor position variables

Inside of a motor there are encoders. These encoders are analog sensors that detect how many times a motor has spun in either direction since the motor gained power. A value of one means the motor spun one time. It can also be represented with a decimal, for example if the value is .5 that motor has done half of a rotation.

```java
    public double getShooterAngleMotorPosition() {
        return this.shooterAngleMotor.getEncoder().getPosition();
    }

    public double getShooterSpeedMotorPosition() {
        return this.shooterSpeedMotor.getEncoder().getPosition();
    }
```

You can use the values to sense where the motors are in space. This means that you can spin a motor until it hits your desired location. You can also set the value of the encoder. The reason for this is because ecoder values are not perfect and after a motor is manipulated for a long period of time the encoder value will become inaccurate. A work around to this is to use a strategy called homing which senses when a limit switch is hit and when it is hit it resets the encoder value to zero. The following functions are used to set the encoder values of the two motors to a desired position.

```java
    public void setShooterAngleMotorPosition(double position) {
        this.shooterAngleMotor.getEncoder().setPosition(position);
    }

    public void setShooterSpeedMotorPosition(double position) {
        this.shooterSpeedMotor.getEncoder().setPosition(position);
    }
```

## Sensor values

The last step in our simple subsystem is a limit switch sensor. The following line gets the value of the sensor and stores it in a variable. When the variable is true that means the switch is being pressed.

```java
    public boolean getShooterButton() {
        return this.shooterButton.get();
    }
```

## Final check up

Your final subsystem should look like this:'

```java
public class Shooter extends SubsystemBase {
    
    public Shooter() {

        this.shooterAngleMotor.setIdleMode(IdleMode.kBrake);
        this.shooterSpeedMotor.setIdleMode(IdleMode.kBrake);

        this.shooterAngleMotor.setInverted(true);
        this.shooterSpeedMotor.setInverted(false);

        this.shooterAngleMotor.setSmartCurrentLimit(50);
        this.shooterSpeedMotor.setSmartCurrentLimit(75);
    }

    public CANSparkMax shooterAngleMotor = new CANSparkMax(1, MotorType.kBrushless);
    public CANSparkMax shooterSpeedMotor = new CANSparkMax(2, MotorType.kBrushless);

    private DigitalInput shooterButton = new DigitalInput(1);

    public enum shooterMotorState {

        ON,
        OFF,
        REVERSED
    }

    public shooterMotorState shooterAngleMotorState = shooterMotorState.OFF;
    public shooterMotorState shooterSpeedMotorState = shooterMotorState.OFF;

    public void setShooterAngleMotorState(shooterMotorState state) {

        this.shooterAngleMotorState = state;
        
        switch (state) {
            case ON:
                this.shooterAngleMotor.set(1);
                break;
            case OFF:
                    this.shooterAngleMotor.set(0);
                break;
            case REVERSED:
                this.shooterAngleMotor.set(-1);
                break;
            default:
                this.setShooterAngleMotorState(shooterAngleMotorState.OFF);
        }
    }
        public void setShooterSpeedMotorState(shooterMotorState state) {

        this.shooterSpeedMotorState = state;
        
        switch (state) {
            case ON:
                this.shooterSpeedMotor.set(1);
                break;
            case OFF:
                    this.shooterSpeedMotor.set(0);
                break;
            case REVERSED:
                this.shooterSpeedMotor.set(-1);
                break;
            default:
                this.setShooterSpeedMotorState(shooterSpeedMotorState.OFF);
        }
    }

    public CANSparkMax getShooterAngleMotor() {
        return this.shooterAngleMotor;
    }

    public CANSparkMax getShooterSpeedMotor() {
        return this.shooterSpeedMotor;
    }

    public double getShooterAngleMotorPosition() {
        return this.shooterAngleMotor.getEncoder().getPosition();
    }

    public double getShooterSpeedMotorPosition() {
        return this.shooterSpeedMotor.getEncoder().getPosition();
    }

    public void setShooterAngleMotorPosition(double position) {
        this.shooterAngleMotor.getEncoder().setPosition(position);
    }

    public void setShooterSpeedMotorPosition(double position) {
        this.shooterSpeedMotor.getEncoder().setPosition(position);
    }

    public boolean getShooterButton() {
        return this.shooterButton.get();
    }
}
```

Congratulations you have completed your simple subsystem!