## Motor states

A motor state refers to the current state or status of a motor within a subsystem of the robot. We will make three diffrent example states with an enum that cantains ON, OFF, and REVERSED.

## Setting motor states

```java
    public enum shooterMotorState {
        ON,
        OFF,
        REVERSED
    }

    public shooterMotorState shooterAngleMotorState = shooterMotorState.OFF;
    public shooterMotorState shooterSpeedMotorState = shooterMotorState.OFF;
```

To define what each of these states do we use function to set the motor states using the enum we made previously.

```java
    public void setShooterAngleMotorState(shooterMotorState state) {
        // set the current state
        this.shooterAngleMotorState = state;
        
        // set motor state
        switch (state) {
            case ON:
                // On
                this.shooterAngleMotor.set(1);
                break;
            case OFF:
                    this.shooterAngleMotor.set(0);
                break;
            case REVERSED:
                // Reversed
                this.shooterAngleMotor.set(-1);
                break;
            default:
                this.setShooterAngleMotorState(shooterAngleMotorState.OFF);
        }
    }

        public void setShooterSpeedMotorState(shooterMotorState state) {
        // set the current state
        this.shooterSpeedMotorState = state;
        
        // set motor state
        switch (state) {
            case ON:
                // On
                this.shooterSpeedMotor.set(1);
                break;
            case OFF:
                    this.shooterSpeedMotor.set(0);
                break;
            case REVERSED:
                // Reversed
                this.shooterSpeedMotor.set(-1);
                break;
            default:
                this.setShooterSpeedMotorState(shooterSpeedMotorState.OFF);
        }
    }
```

These functions define how each state value will manipulate the motor. The on state makes the motor go clockwise at max speed (the max speed is 1) and off makes the motor not move. 

## Checkup!

Here is what your subsystem should look like so far:

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
}
```