# AAOS Architecture

``` text
Driver touches screen
↓
App (Kotlin / Java)
↓
Android Framework
(Binder IPC)
↓
Car Service
(Java / Kotlin)
↓
AIDL
↓
Vehicle HAL (VHAL)
(C++)
↓
Vehicle Middleware
(C++ / SOME/IP / DDS / custom)
↓
Vehicle Network
(CAN / LIN / Ethernet)
↓
ECUs
(C / C++ / AUTOSAR)
↓
Real car thing happens
```

## 1. App layer

Languages: - Kotlin - Java - Compose

Concepts: - Activity - Service - Flow - ViewModel - StateFlow

Example:

``` kotlin
carPropertyFlow.collect {
   updateUi(it)
}
```

Flow = reactive updates.

------------------------------------------------------------------------

## 2. Android Framework

Languages: - Java - Kotlin - Some C++

Protocols: - Binder IPC

Think: normal Android kingdom.

------------------------------------------------------------------------

## 3. Car Service

Languages: - Mostly Java - Some Kotlin

Protocols: - Binder - AIDL

Examples: - CarPropertyManager - CarPowerManager - CarAudioManager

``` text
getSpeed()
↓
Binder
↓
Car Service
```

------------------------------------------------------------------------

## 4. AIDL

Protocol: - Binder

Generated for: - Java - Kotlin - C++

``` aidl
interface IClimate {
  void setTemp(int value);
}
```

Think: Android local RPC.

------------------------------------------------------------------------

## 5. Vehicle HAL (VHAL)

Languages: - C++

Protocols: - AIDL (new) - HIDL (older)

``` text
setProperty()
↓
Vehicle HAL
↓
ECU
```

Think: Android ↔ Car adapter.

------------------------------------------------------------------------

## 6. Middleware

Languages: - Mostly C++

### SOME/IP

Service-oriented communication.

``` text
Request speed
←→
Response
```

### DDS

Publish / Subscribe.

``` text
publish(speed)
subscribe(speed)
```

### gRPC

``` proto
service Climate {
 rpc SetTemp(Request)
}
```

Uses protobuf.

### Protobuf

``` proto
message Speed {
 int32 value = 1;
}
```

Binary data format.

------------------------------------------------------------------------

## 7. Vehicle networks

-   CAN
-   CAN FD
-   LIN
-   Ethernet
-   DoIP
-   FlexRay
-   MOST

------------------------------------------------------------------------

## 8. ECUs - Actual hardware brains.
Each controls real things.

-   HVAC ECU
-   Cluster ECU
-   Body ECU
-   ADAS ECU

------------------------------------------------------------------------

## Modern 2026 stack

``` text
Compose
↓
StateFlow
↓
ViewModel
↓
Repository
↓
AIDL
↓
Car Service
↓
VHAL
↓
SOME/IP
↓
ECU
```

Quick memory: - Flow = async data - AIDL = Android talks - Proto =
compact data - SOME/IP = car talks - CAN = wire talks


