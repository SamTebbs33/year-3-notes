# Location-based services

## Satellites
Transmit their current time using regularly synced atomic clocks, and their current location which is precisely known and controlled.

## Receivers
Receive the radio waves (~1600 mHz), uses simultaneous equations to calculate longitude, latitude and elevation.

## Assistance
Cell towers know where they are and can relay this information to devices.

Google knows where you are when you pair with WiFi access points. A database of connections between WiFi and location can be built and shared.

## Positioning types

### Absolute positioning
You're at 52˚27'03.7"N, 01˚55'43.1W

Allows for precise positioning, but unintelligible to people.

### Symbolic positioning
You're at home. The Prime Minister is at 10 Downing Street.

Easy for people to understand and good where unambiguous categories exist (wat?).

### Relative positioning
You're 4.3m from the door.

Relatively easy to understand while providing higher precision.

## Sources of error
* **Signal delay**: Conditions in the ionosphere affect speed of signal
* **Reflections**: Signals are reflected (e.g. off buildings) or bent, altering arrival time

### Representing measurement error
* **Pessimistic**: Lost, don't know where I am
* **Optimistic**: Pretending to be sure, no error indication
* **Cautious**: Showing what you know and indicating error
* **Opportunistic**: I'm not sure, but let's let user figure out how to handle the error (pirate GPS game)

![Cautious measurement example](img/cautious_gps.png)
