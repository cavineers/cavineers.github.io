# Command Compositions

Commands in the command-based library are capable of performing a variety of robot tasks. However, when **advanced functionality requiring extended sequences of robot tasks or coordination of multiple robot subsystems** is required, users are encouraged to use the **command composition** functionality.


!!! question "Question"

    Where do you think 4541's Software Team uses compositions the most?

??? success "One Answer"

    4541, along with pretty much every FRC team, uses command compositions in their autonomous routines. You will learn more about this in the Autonomous Section!

!!! note inline end "Component Commands"

    Component Commands --> Any command

A **command composition** is a combination of one or more commands that allows code to be kept cleaner and simpler. **Component commands can be written independently of the code that combines them, reducing complexity.**

**Command compositions are commands themselves**, which allows them to be **further composed as a recursive composition**. This means a command composition can contain other command compositions as components, enabling **powerful and concise inline expressions**.

!!! note "Commands Themselves"

    Because they are commands themselves, compositions inherit the [standard properties](../../Commands/properties.md) of commands.
    
