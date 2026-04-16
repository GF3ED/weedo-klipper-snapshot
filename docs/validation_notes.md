# Validation notes (Klipper IDEX config)

Queste note tracciano i riferimenti usati per strutturare il config in modo coerente:

- Klipper Config Reference (`dual_carriage`, `extruder1`, `homing_override`).
- Klipper G-Codes (`SET_DUAL_CARRIAGE`, `ACTIVATE_EXTRUDER`).
- Pattern macro IDEX (tool-select T0/T1 con carrello 0/1).

## Test eseguiti in repository
- Verifica di presenza sezioni principali (`extruder1`, `tmc2209 extruder1`, `T0/T1`, `homing_override`).
- Verifica base di bilanciamento token Jinja (`{%` / `%}` e `{{` / `}}`) su `macro.cfg`.
- Verifica `git diff --check` per whitespace e marker anomali.
- Verifica incrociata mapping termistori/heater con dati utente:
  - `J44/PF3` (bed), `J45/PF4` (H0), `J46/PF5` (H1)
  - `H0/PA2`, `H1/PA3`
- Verifica conflitti sezione tra `printer.cfg`, `macro.cfg`, `mainsail.cfg` (nessun duplicato di sezione).

## Limite ambientale
In questa sandbox non è presente un'istanza Klipper/Sonic Pad avviabile con MCU virtuale collegata, quindi non è possibile fare un dry-run firmware completo equivalente alla macchina fisica.

## Checklist pre test fisico consigliata
- Eseguire `DEBUG_IDEX_CFG` dopo `RESTART`.
- Eseguire `G28` e poi `TEST_T1`.
- Verificare che i pin termici rilevino temperatura ambiente coerente:
  - `extruder` (J45/PF4), `extruder1` (J46/PF5), `heater_bed` (J44/PF3).
- Verificare che il pin `enable_pin` di `dual_carriage` (`!PA0` in cfg) corrisponda al cablaggio reale della board montata.
