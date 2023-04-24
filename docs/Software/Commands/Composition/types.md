# Composition Types

## Repeatedly Composition

!!! quote "Repeatedly Composition"
    The `repeatedly()` decorator, backed by the `RepeatCommand` class restarts the command each time it ends, so that it runs until interrupted.

!!! example "Decorator"
    ``` java 
    Command repeats = exampleCommand.repeatedly();
    ```

The command is restarted by calling the command's `execute()` method again. The command is interrupted by calling the command's `end()` method. 

!!! example "Canceling a Repeatedly Command"
    ``` java 
    Command repeats = exampleCommand.repeatedly();
    // Assuming the command is scheduled
    repeats.cancel();
    ```

## Sequential Composition

Arguably one of the most important composition type, the `SequentialCommand` class runs a list of commands in sequence. The command ends when the last command in the sequence ends.

Sequential Compositions can be created in a variety of ways:

=== "Using SequentialCommand Constructor"

    ``` java 
    Command sequential = new SequentialCommand(exampleCommand, exampleCommand2);
    ```

=== ".andThen() Decorator"

    ``` java
    Command sequential = exampleCommand.andThen(exampleCommand2);
    ```

=== "SequentialCommandGroup Class"

    ``` java 
    Command sequential = new SequentialCommandGroup(exampleCommand, exampleCommand2, exampleCommand3);
    // OR
    Command sequential = new SequentialCommandGroup()
    
    sequential.addCommands(exampleCommand, exampleCommand2, exampleCommand3);
    ```

!!! question "What's the difference between a SequentialCommand and SequentialCommandGroup?"

    The main difference between the two is that a `SequentialCommandGroup` allows you to group multiple commands together as a **single command**. This means that you can create a complex series of actions, like moving an arm, then closing a claw, then raising the arm again, and execute them all as a **single command**.


## Parallel Composition

Another important composition type, the `ParallelCommand` class runs a list of commands in parallel. The command ends when the last command in the sequence ends.

Parallel Compositions can be created in a variety of ways:

=== "Using ParallelCommand Constructor"

    ``` java 
    Command parallel = new ParallelCommand(exampleCommand, exampleCommand2);
    ```

=== ".alongWith() Decorator"

    ``` java
    Command parallel = exampleCommand.alongWith(exampleCommand2);
    ```
=== "ParallelCommandGroup Class"

    ``` java
    Command parallel = new ParallelCommandGroup(exampleCommand, exampleCommand2, exampleCommand3);
    // OR
    Command parallel = new ParallelCommandGroup()

    parallel.addCommands(exampleCommand, exampleCommand2, exampleCommand3);
    ```

!!! question "What's the difference between a ParallelCommand and ParallelCommandGroup?"

    ```ParallelCommandGroup``` is used when you want to group commands together as a **single logical unit.** <br>   ```ParallelCommand``` is used when you want to run multiple commands **independently and concurrently.**



