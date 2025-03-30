# isaver-RS485-modbus-
NVERSilence, Madimack, Rapid X20, AtecPool, Trendpool, Vario, AquaForte, Vitalia, Aquagripp, Aquagem iSaver pool inverter


further links:
https://community.home-assistant.io/t/modbus-isaver-pool-pump-inverter-custom-commands-issue-response-mising-bytes/714637

iSaverX display pcb CN3

---+---+---+---+---+---+---+---+---+---
  GND V/I  B   A  GND IN1 IN2 IN3 IN4
|--------|-------|--------------------|

analog Input

RS485
 
digital Input
- GND: ground
- IN1: On/Off
- IN2: 2900rpm (backwash)
- IN3: 2400rpm (day mode)
- IN4: 1200rpm (night mode)

usage:
 For example – to enable external speed control via digital input, connect one of the digits from Di2/3/4 to COM
