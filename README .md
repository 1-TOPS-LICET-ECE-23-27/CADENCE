README – Creating Layout from Schematic in Cadence Virtuoso

This guide explains how to create a layout in Cadence Virtuoso using an existing schematic.
It includes opening the schematic, generating the layout view, placing devices, assigning taps, connecting metals, and basic checks.

1. Open the Schematic

In the Library Manager, select your library → cell → schematic view.

Open the schematic and verify:

VDD and GND pins exist

Instances (PMOS, NMOS, etc.) are named correctly

No missing connections or floating nets

From the menu:
Launch → Layout XL
or
Create → Layout → XL

2. Initialize Layout XL

When prompted, select:
“Open Existing → Schematic”

In the comments/options window, keep the same settings and continue.

Virtuoso LayoutXL opens with:

Device placement assistant

Connectivity information from the schematic

Auto pins and matching nets

3. Generate the Layout

In the Layout XL window, click:
Design → Generate From Source

Choose:

Pins: Yes

Devices: Yes

Nets: No (if doing manual routing)

Press OK.

The tool will place:

PMOS and NMOS transistors

VDD/GND pins

give shift+F -> for the internal view of the transistors

4. Edit Device Properties

Select each MOSFET → Right-click → Properties → Parameters:

For PMOS

Body type: detached

Body contact: left tap

For NMOS

Body type: default or left tap

Adjust if needed based on PDK rules.

This ensures:

PMOS connects to VDD through a tap

NMOS connects to GND through a tap

5. Arrange Devices

Move PMOS to the top (near VDD).

Move NMOS to the bottom (near GND).

Maintain:

Minimum spacing rules

Alignment for clean routing

Proper diffusion and poly orientation

Use m to move, q for properties.

6. Remove Unnecessary Sources

If the schematic had sources (VDD, VIN, etc.) used for simulation:

Delete them from layout generation

Only keep pins and MOSFETs

Ensure net names (e.g., VIN, VOUT) are correct

7. Create Connections

Use metal1 to connect:

NMOS source → GND

PMOS source → VDD

Use poly for gate connections.

Maintain minimum spacing and boundary rules:

Gate-to-gate spacing

Diffusion boundaries

Metal spacing (e.g., 0.12 µm)

If required, add:

Contacts

Vias

Metal2 or higher layers for crossing

8. Check DRC and LVS
DRC (Design Rule Check)

Run:
Verify → DRC
Fix:

Spacing violations

Overlapping metals

Missing contacts

Boundary violations

LVS (Layout vs Schematic)

Run:
Verify → LVS
Ensure:

Net names match

Device count matches

No floating nets

9. Final Steps

Label nets properly

Add pin layers (e.g., metal1_pin)

Save and re-run checks

Export GDS if required

Conclusion

This README provides a step-by-step procedure for generating and editing a Cadence Virtuoso layout from a schematic. It covers:

Opening the schematic

Generating layout with XL

Editing MOSFET properties

Creating proper taps

Performing routing

Running DRC/LVS
