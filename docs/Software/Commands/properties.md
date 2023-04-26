# Command Properties

In addition to the four lifecycle methods, each Command in the WPILib library has three properties that can be set to customize its behavior. These properties are defined by getter methods and should always return the same value with no side effects.

## `getRequirements()`

Declares any subsystems that the command controls as requirements. This property ensures that no more than one command requires a given subsystem at the same time, preventing conflicts such as two different pieces of code attempting to set the same motor controller to different output values.

This property can be set by:

- Overriding the `getRequirements()` method in the relevant command class
- Calling `addRequirements()` method
- Using the `requirements` vararg parameter

???+ example "Adding Requirements to a Command"

    ```java
    public class ExampleCommand extends CommandBase {
        private final ExampleSubsystem m_subsystem;

        public ExampleCommand(ExampleSubsystem subsystem) {
            m_subsystem = subsystem;
            // Use addRequirements() here to declare subsystem dependencies.
            addRequirements(subsystem);
        }
    }
    ```

## `runsWhenDisabled()`

Specifies whether the command may run when the robot is disabled. By default, the value is `false`, meaning the command will be canceled when the robot is disabled and attempts to schedule it will do nothing. Returning `true` will allow the command to run and be scheduled when the robot is disabled.

This property can be set by:

- Overriding the `runsWhenDisabled()` method in the relevant command class
- Using the `ignoringDisable` decorator

???+ example "Adding Requirements to a Command"

    ```java hl_lines="7 8 9"
    public class ExampleCommand extends CommandBase {

        public ExampleCommand() {
           
        }

        boolean runsWhenDisabled(){
            return true; // Allows the command to run while disabled
        }
    }
    ```



## `getInterruptionBehavior()`

Defines what happens if another command sharing a requirement is scheduled while this one is running. The default behavior is `kCancelSelf`, meaning the current command will be canceled and the incoming command will be scheduled successfully. If `kCancelIncoming` is returned, the incoming command’s scheduling will be aborted and this command will continue running.

This property can be set by:

- Overriding the `getInterruptionBehavior()` method in the relevant command class
- Using the `withInterruptBehavior()` decorator (Java, C++).
