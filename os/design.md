# Goals
## User goals
* Convenient to use
* Easy to learn
* Reliable
* Safe
* Fast

## System goals
* Easy to design
* Easy to implement
* Easy to maintain

# Policies and mechanisms
Separation of policy from mechanism is an important principle as it allows maximum flexibility if policy decisions are to be changed later.

An architecture that supports various filesystems, rather than having one hard-coded is an example

## Policy
What will be done?

## Mechanism
How is it to be done?

# Layering
An OS layer only deals with the layer below it, to enforce stability and modularity. Layer 0 is the hardware and layer N is the user-interface layer
