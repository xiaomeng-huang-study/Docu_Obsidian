```plantuml
@startuml
skinparam groupInheritance 1
skinparam linetype ortho


package "Interfaces"{
interface IButtons #Tomato
interface IMotors #Tomato
interface ISensors #Tomato
interface IDisplay #Tomato
interface IBuzzer #Tomato
interface IEncoders #Tomato
interface IBattery #Tomato
interface ILEDs #Tomato
}

package "Classes"{
class FollowALine
class Calibration
class StoreSystemTime
class DisplayLapTime
class LostTrackHandler
class HardwareError
class SoftwareError
}

package ""{
class PololuMotors #LightGreen
class PololuSensors #LightGreen
class PololuOLED #LightGreen
class PololuBuzzer #LightGreen
class PololuEncoders #LightGreen
class PololuBattery #LightGreen
class PololuLEDs #LightGreen
class PololuButtons #LightGreen
}

package "Polulu Library"{
class Zumo32U4 {
	+ledRed()
	+ledGreen()
	+ledYellow()
	+usbPowerPresent()
	+readBatteryMillivolts()	
}


class Zumo32U4OLEDCore {
	+initPins() : void
	+reset() : void
	+sh1106CommandMode() : void
	+sh1106DataMode() : void
	+sh1106TransferEnd() : void
	+sh1106TransferStart() : void
	+sh1106Write(uint8_t d) : void
}

class Zumo32U4ButtonA {
	+isPressed() : bool
	+getSingleDebouncedPress() : bool
	+getSingleDebouncedPress() : bool
	+waitForPress() : void
	+waitForRelease() : void
	+waitForButton() : void
}


class Zumo32U4ButtonB {
	+isPressed() : bool
	+getSingleDebouncedPress() : bool
	+getSingleDebouncedPress() : bool
	+waitForPress() : void
	+waitForRelease() : void
	+waitForButton() : void
}


class Zumo32U4ButtonC {
	+isPressed() : bool
	+getSingleDebouncedPress() : bool
	+getSingleDebouncedPress() : bool
	+waitForPress() : void
	+waitForRelease() : void
	+waitForButton() : void
}


class Zumo32U4Encoders {
	+{static} checkErrorLeft() : bool
	+{static} checkErrorRight() : bool
	+{static} getCountsAndResetLeft() : int16_t
	+{static} getCountsAndResetRight() : int16_t
	+{static} getCountsLeft() : int16_t
	+{static} getCountsRight() : int16_t
	+{static} init() : void
}

class Zumo32U4Motors {
	+{static} flipLeftMotor(bool flip) : void
	+{static} flipRightMotor(bool flip) : void
	+{static} init() : void
	+{static} setLeftSpeed(int16_t speed) : void
	+{static} setRightSpeed(int16_t speed) : void
	+{static} setSpeeds(int16_t leftSpeed, int16_t rightSpeed) : void
}


class Zumo32U4Buzzer {
	
	+{static} playFrequency (unsigned int freq, unsigned int duration, unsigned char volume) : void
	+{static} playNote (unsigned char note, unsigned int duration, unsigned char volume) : void
	+{static} play (const char *sequence) : void
	+{static} playFromProgramSpace (const char *sequence) : void
	+{static} playMode (unsigned char mode) : void
	+{static} playCheck () : char
	+{static} isPlaying () : char
	+{static} stopPlaying () : void

}


class Zumo32U4LineSensors {
	+Zumo32U4LineSensors()
	+Zumo32U4LineSensors(uint8_t* pins, uint8_t numSensors, uint8_t emitterPin)
	+init(uint8_t* pins, uint8_t numSensors, uint16_t timeout, uint8_t emitterPin) : void
	+initFiveSensors(uint8_t emitterPin) : void
	+initThreeSensors(uint8_t emitterPin) : void
}



Zumo32U4 --|> Zumo32U4ButtonA
Zumo32U4 --|> Zumo32U4ButtonB
Zumo32U4 --|> Zumo32U4ButtonC
Zumo32U4 --|> Zumo32U4OLEDCore
Zumo32U4 --|> Zumo32U4Buzzer
Zumo32U4 --|> Zumo32U4Encoders
Zumo32U4 --|> Zumo32U4LineSensors
Zumo32U4 --|> Zumo32U4Motors



Zumo32U4ButtonA --* PololuButtons
Zumo32U4ButtonB --* PololuButtons
Zumo32U4ButtonC --* PololuButtons
Zumo32U4OLEDCore --* PololuOLED
Zumo32U4Buzzer --* PololuBuzzer
Zumo32U4Encoders --* PololuEncoders
Zumo32U4LineSensors --* PololuSensors
Zumo32U4Motors --* PololuMotors
Zumo32U4 --* PololuBattery
Zumo32U4 --* PololuLEDs

}

PololuButtons ..|> IButtons
PololuOLED ..|> IDisplay
PololuBuzzer ..|> IBuzzer
PololuEncoders ..|> IEncoders
PololuSensors ..|> ISensors
PololuMotors ..|> IMotors
PololuBattery ..|> IBattery
PololuLEDs ..|> ILEDs

IEncoders --o HardwareError
IButtons --o FollowALine
IButtons --o Calibration
IMotors --o FollowALine
IMotors --o Calibration
ISensors --o FollowALine
ISensors --o Calibration

FollowALine --o LostTrackHandler
IMotors --o LostTrackHandler
ISensors --o LostTrackHandler

DisplayLapTime o-- IDisplay
DisplayLapTime --o StoreSystemTime

SoftwareError o-- FollowALine
SoftwareError o-- LostTrackHandler
SoftwareError --o IDisplay
SoftwareError --o IBuzzer
SoftwareError --o ILEDs

HardwareError o-up- IMotors
HardwareError o-up- ISensors
HardwareError o-up- IBattery
HardwareError -up-o IDisplay
HardwareError -up-o IBuzzer
HardwareError --o ILEDs

@enduml
```