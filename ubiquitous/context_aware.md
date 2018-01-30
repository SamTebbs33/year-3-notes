# Context aware computing
Machines need to understand context as well as moment-to-moment contextual changes.

## Embeddedness (?)
Devices are becoming more and more embedded in our lives, meaning developers have less control of the context in which they are used.

## Types of context

### Computing context
Wireless interference, technology available.

### Physical context
Differing environments (jungle, coffee shop, space etc.)

### User environment
People's background, age, roles, mannerisms, prestige etc.

## Features of context awareness

### Presentation
Serving people information that is relevant to the current context. For example, offering information to museum visitors based on where they are in the building, the exhibit they're looking at, or their own preferences etc.

### Execution
Performing actions based on current context. For example turning on the lights when movement is detected in a room.

### Tagging
Understanding context at a given moment for later retrieval. For example keeping track of when people respond to notifications for later use.

## Designing for context
The example system is one for sharing awareness of activity in a room
1. **Specification**: Light up LEDs depending on activity in a room
2. **Acquisition**: Write software to analyse motion changes from camera
3. **Delivery**: Make activity info available using pub-sub system
4. **Reception**: Application wants to receive changes in activity
5. **Action**: Light up LEDs
