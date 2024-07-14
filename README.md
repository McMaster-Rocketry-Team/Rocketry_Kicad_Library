# Rocketry Shared Kicad Library

- `Rocketry_Easyeda`: symbols and footprints imported using easyeda2kicad
- `Rocketry_Manual`: symbols and footprints imported manually

## Installing the Library

1. Clone the repo
2. KiCad -> Preferences -> Configure Paths
   1. Add Name: `ROCKETRY_LIBRARY`, Path: `<Path of the cloned repo>`
3. KiCad -> Preferences -> Manage Symbol Libraries
   1. Add Nickname: `Rocketry_Easyeda`, Library Path: `${ROCKETRY_LIBRARY}/Rocketry_Easyeda.kicad_sym`
   2. Add Nickname: `Rocketry_Manual`, Library Path: `${ROCKETRY_LIBRARY}/Rocketry_Manual.kicad_sym`
4. KiCad -> Preferences -> Manage Footprint Libraries
   1. Add Nickname: `Rocketry_Easyeda`, Library Path: `${ROCKETRY_LIBRARY}/Rocketry_Easyeda.pretty`
   2. Add Nickname: `Rocketry_Manual`, Library Path: `${ROCKETRY_LIBRARY}/Rocketry_Manual.pretty`

## Using [easyeda2kicad](https://pypi.org/project/easyeda2kicad/)

easyeda2kicad imports symbols and footprints from JLCPCB. (Note: before using easyeda2kicad, first check if KiCad already has the component in its built-in libraries!)

1. Install by running `pip install easyeda2kicad` in the shell
2. Find the component you want to use on https://jlcpcb.com/parts/
3. Run in the shell:
   ```sh
   easyeda2kicad --output <Path of the cloned repo>/Rocketry_Easyeda --symbol --footprint --lcsc_id=<Component ID, starts with C>
   ```

## Manually Import Symbols and Footprints

If easyeda2kicad does not have the component you need, you can download symbols and footprints manaully.

Websites to find symbols and footprints:

- https://www.snapeda.com/
- https://www.ultralibrarian.com/

### Import Footprints

Sometimes you only need to import a footprint, as the symbol is already in the built-in libraries (e.g. connectors)

To do that, just copy the downloaded `*.kicad_mod` file into `<Path of the cloned repo>/Rocketry_Manual.pretty`

### Import Symbols

We need to merge the downloaded `*.kicad_sym` file with the existing `Rocketry_Manual.kicad_sym` file.

1. Install a tool by running `pip install merge-kicad-sym` in the shell
2. Run in the shell `merge-kicad-sym --overwrite-footprint-lib-name Rocketry_Manual <Path of the cloned repo>/Rocketry_Manual.kicad_sym <path of downloaded .kicad_sym>`

## Notes on Git

Remember to commit, push and pull!
