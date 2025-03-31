# isaver-RS485-modbus-
NVERSilence, Madimack, Rapid X20, AtecPool, Trendpool, Vario, AquaForte, Vitalia, Aquagripp, Aquagem iSaver pool inverter


further links:
https://community.home-assistant.io/t/modbus-isaver-pool-pump-inverter-custom-commands-issue-response-mising-bytes/714637

Connection:
- iSaverX display pcb CN3
- JST-PH-9 2mm distance

---+---+---+---+---+---+---+---+---+---
  GND V/I  B   A  GND IN1 IN2 IN3 IN4
|-analog-|-RS485-|---digital----------|

analog Input
- not tested

RS485 
-> this is not standard modbus rtu!!!
-> so it won#t work with standard implementations
-> check protocol.pdf: 1200-8-N-1; default slave 0xAA(170)

precondition:
- power on inverter manually!
- now you can change rpm or turn off/on again
- if power off manually, you can't wakeup inverter by rs485
- after wake up, inverter is using max rpm for 60sec, afterwards switching to commanded rpm

READ -> 0xC3 Command not 0x03 like standard modbus
AA C3 07 D1 00 00 0D 4D
RESPONSE
AA C3 00 00 01 05 46 D3 5B

WRITE 2000rpm -> D0 Command
AA D0 0B B9 07 D0 09 AE
RESPONSE
AA D0 0B B9 00 02 00 83 67

WRITE off (1rpm)
AA D0 0B B9 00 01 CB C2
RESPONSE
AA D0 0B B9 00 02 00 83 67

 
digital Input
- GND: ground
- IN1: On/Off
- IN2: 2900rpm (backwash)
- IN3: 2400rpm (day mode)
- IN4: 1200rpm (night mode)

usage:
 For example – to enable external speed control via digital input, connect one of the digits from Di2/3/4 to COM
