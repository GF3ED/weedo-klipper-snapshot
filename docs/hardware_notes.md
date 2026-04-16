# Hardware notes (from user-provided mapping)

## Platform
- Board: BTT Octopus Pro V1.1 (STM32F446)
- Chassis: Weedo X40 V2 PRO
- Firmware stack: Klipper on Sonic Pad Debian mod
- Z Probe: BIQU MicroProbe

## Pinout / driver mapping

| Driver | Funzione | STEP | DIR | ENABLE | UART | Stato |
|--------|----------|------|-----|--------|------|-------|
| Driver0 | Y | PF13 | PF12 | !PF14 | PC4 | ✔ ATTIVO |
| Driver1 | X1 (sinistra, probe) | PG0 | !PG1 | !PF15 | PD11 | |
| Driver2 | Z | PF11 | PG3 | !PG5 | PC6 | |
| Driver3 | X2 (destra) | PG4 | PC1 | !PA2 | PC7 | |
| Driver4 | EXTRUDER | PF9 | PF10 | !PG2 | PF2 | |
| Driver5 | EXTRUDER 1 | PC13 | PF0 | !PF1 | PE4 | |
| Driver6 | NON USATO | PE2 | !PE3 | !PD4 | PE1 | |
| Driver7 | NON USATO | PE6 | PA14 | !PE0 | PD3 | |

### UART status
- Driver0 Y: ✔ UART
- Driver1 X1: ✔ UART
- Driver2 Z: ✔ UART (anche con MicroProbe)
- Driver3 X2: ✔ UART
- Driver4 E0: tutti e 4 (standalone o SPI, non UART standard)
- Driver5 E1: tutti e 4 (idem)
- Driver6/7: vuoti

Nota: nel testo originale l'utente indica che i ponticelli driver/diag 0..7 sono stati cablati correttamente.

## Nota implementativa extruder1
- In `klipper/printer.cfg` `extruder1` è stato reso attivo con mapping step/dir/enable/uart coerente alla tabella (`PC13/PF0/!PF1/PE4`).
- Mapping termico impostato (coerente con tua nota):
  - Bed thermistor `J44` -> `PF3`
  - Hotend0 thermistor `J45` -> `PF4`
  - Hotend1 thermistor `J46` -> `PF5`
  - Heater H0 -> `PA2`
  - Heater H1 -> `PA3`
- Nota di coerenza: su alcuni materiali BTT per varianti diverse di Octopus Pro compare `HE0=PA0`; per questa configurazione resta `PA2` perché coerente con i dati macchina forniti e con il setup già in uso.
