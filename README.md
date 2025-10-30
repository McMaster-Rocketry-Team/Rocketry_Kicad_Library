# Rocketry Shared Kicad Library

- `Rocketry_Easyeda`: symbols and footprints imported using easyeda2kicad
- `Rocketry_Manual`: symbols and footprints imported manually

## Installing the Library

1. Clone the repo 
2. KiCad -> Preferences -> Configure Paths
   1. Add Name: `ROCKETRY_LIBRARY`, Path: `<Path of the cloned repo>`
3. KiCad -> Preferences -> Manage Symbol Libraries
   1. Add Nickname: `Rocketry_Easyeda`, Library Path: `${ROCKETRY_LIBRARY}/Rocketry_Easyeda.kicad_sym` (copy and paste this exactly)
   2. Add Nickname: `Rocketry_Manual`, Library Path: `${ROCKETRY_LIBRARY}/Rocketry_Manual.kicad_sym` (copy and paste this exactly)
4. KiCad -> Preferences -> Manage Footprint Libraries
   1. Add Nickname: `Rocketry_Easyeda`, Library Path: `${ROCKETRY_LIBRARY}/Rocketry_Easyeda.pretty` (copy and paste this exactly)
   2. Add Nickname: `Rocketry_Manual`, Library Path: `${ROCKETRY_LIBRARY}/Rocketry_Manual.pretty` (copy and paste this exactly)

## Using [easyeda2kicad](https://pypi.org/project/easyeda2kicad/)

easyeda2kicad imports symbols and footprints from JLCPCB. (Note: before using easyeda2kicad, first check if KiCad already has the component in its built-in libraries!)

1. Install by running `pip install easyeda2kicad` in the shell
2. Find the component you want to use on https://jlcpcb.com/parts/
3. Run in the shell:
   ```sh
   git pull
   easyeda2kicad --output <Path of the cloned repo>/Rocketry_Easyeda --symbol --footprint --lcsc_id=<Component ID, starts with C>
   ```
4. When importing JLC "basic" resistors and capacitors, rename the symbol in Kicad to the following format: "Part_number (size value)", eg "C14N3 (0603 120uF)".
   This keeps our component library easy to search!
5. Commit and push

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

## Manually Create Symbols and Footprints

Just follow the usual steps to create symbols and footprints in the "Rocketry_Manual" libraries.

## Notes on Git

Remember to commit, push and pull!
