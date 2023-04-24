# Structure of a Command

## States
When writing a command, you need to specify what the command should do in each of its possible states. To do this, you override the ```initialize()```, ```execute()```, and ```end()``` methods. The command should also be able to tell the scheduler when it has finished executing by overriding the `isFinished()` method.

!!! tip "end() Method"

    The `end()` method actually provides a parameter to check if the command ended normally, or was interrupted.

    ``` java
        void end(boolean interrupted){
            if (interrupted == True){
                // The command has been interrupted
            }
            else{
                // The command has ended as expected
            }
        }
    ```

!!! tip inline end
    
    If a command is not finishing correctly, make sure the ```isFinished()``` method returns true when the command should terminate

### Default Behavior
If you don't want to specify any special behavior for these methods, they are already provided with default behavior. For example, ```initialize()```, ```execute()```, and ```end()``` do <b>nothing</b> by default, while `isFinished()` returns <b>false</b> by default. This creates a command that runs <b>indefinitely</b> until it is interrupted.


!!! info "Methods in Summary"

    ```initialize()``` --> Called once per scheduling <br>
    ```execute()``` --> Called every scheduler cycle that the command is scheduled <br>
    ```end()``` --> Runs once per termination (at the end) <br>
    ```isFinished()``` --> Called every scheduler cycle (if true --> terminate command)

