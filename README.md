# winmp

Repository con configurazione Klipper per Weedo X40 V2 IDEX (Octopus Pro F446).

## File principali
- `klipper/printer.cfg`: configurazione hardware/driver/termiche ordinata (senza macro monolitiche).
- `klipper/macro.cfg`: macro IDEX (`T0`/`T1`), homing personalizzato, probe helper e test T1.
- `klipper/mainsail.cfg`: copia di riferimento delle client macro originali.
- `klipper/mainsail1.cfg`: client macro set attivo incluso da `printer.cfg` (modificabile senza toccare il file originale in macchina).
- `docs/hardware_notes.md`: note hardware e mappatura pin fornite dall'utente.
- `docs/validation_notes.md`: note di validazione e limiti dell'ambiente di test.

## Note rapide T1
- La macro `T1` è ora definita e seleziona il carrello destro.
- `extruder1` è definito nel `printer.cfg` e viene usato da `T1` tramite `_T1_CONFIG`.
- Macro di test inclusa: `TEST_T1` (movimento X destro/sinistro senza estrusione).
- Macro diagnostica inclusa: `DEBUG_IDEX_CFG` (verifica coerenza estrusore associato a T1).
- Macro homing dedicate incluse: `HOME_X1` / `HOME_X2` (focus toolhead sinistro/destro).

## Note operative ventole / estrusori
- `board_fan` e `hotend_fan_t0` sono configurate come `fan_generic` (controllo manuale da UI/comando `SET_FAN_SPEED`).
- `extruder` (T0) usa ora il mapping Driver4 (`PF9/PF10/!PG2`, UART `PF2`) coerente con il pinout hardware dichiarato.
