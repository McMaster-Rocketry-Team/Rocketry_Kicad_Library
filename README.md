# Rocketry Shared Kicad Library

Instructions comming.....

- `Rocketry_Easyeda`: symbols and footprints imported using easyeda2kicad
- `Rocketry_Manual`: symbols and footprints imported manually

## Using easyeda2kicad

Replace `~/Rocketry_Kicad_Library` with the path of the cloned repo. Replace `C0000` with the id of the actual component.

```sh
easyeda2kicad --output ~/Rocketry_Kicad_Library/Rocketry_Easyeda --symbol --footprint --lcsc_id=C0000
```
