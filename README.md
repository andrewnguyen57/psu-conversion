# ATX Bench Power Supply Conversion

<p align="center">
  <img src="images/final-product.png" width="700">
</p>

<p align="center">
Converting ATX computer power supplies into high power benchtop power supplies
</p>

---

# Table of Contents

- [Project Overview](#project-overview)
- [Why I Built This](#why-i-built-this)
- [Case Design](#case-design)
- [Electrical Diagram](#electrical-diagram)
- [Build Process](#build-process)
- [Bill of Materials](#bill-of-materials)
- [Video](#video)

---

# Safety Warning

This project involves working with mains AC voltage and high power circuitry.

Attempt this project at your own risk.

Large capacitors inside ATX power supplies can retain dangerous voltages even after unplugging the unit.

---

# Project Overview

This project converts a standard Desktop ATX Power Supply into a benchtop power supply.
The design implements 3V3, 5V, and 12V outputs along with a variable voltage module output.

---

# Final Result

<p align="center">
  <img src="images/final-front.png" width="350">
  <img src="images/final-powered-on.png" width="350">
</p>

<p align="center">
  <img src="images/final-inside.png" width="500">
</p>

---

# Why I Built This

Personally, this was an extremely rewarding project for me to build.

It seems very easy on the surface, but I ran into countless problems and almost gave up many times. By sticking through all the difficulties, I learned a lot and had a lot of fun throughout the process.

I highly recommend trying a project like this if you are interested in electronics and electrical engineering.

Economically, benchtop power supplies are sold everywhere on Amazon, AliExpress, and many other places, but they are usually very expensive.

ATX power supplies are generally inexpensive while being capable of delivering a huge amount of power.

For example, the power supply I used in this project can output:

- 22A at 3V3
- 25A at 5V
- 36A at 12V

That is an incredible amount of power, and a comparable off-the-shelf benchtop power supply would cost significantly more.

---

# Case Design

<p align="center">
    <img src="images/case-design.png" width="450"><br>
    <em>Case 3D Model Design</em>
</p>

I designed this case specifically for my PSU, but it should fit most ATX power supplies in the 450W–650W range.

I would not recommend using extremely large power supplies because:

- They are physically too large
- Most of their output capability will never actually be used in this design

The case is designed to support:

- 3V3 output
- 5V output
- 12V output
- Variable voltage output using the ZK4KX/ZK5KX module

---

# Electrical Diagram

- [Wiring Diagram](docs/wiring-diagram.pdf)

---

# Build Process

This is documentation of my build process, not a full tutorial.
If you follow my steps, do so at your own risk. Knowledge of electrical engineering is highly recommended.

### PSU Selection

For this project, I chose to use a Cooler Master Elite 500W V2 power supply from a retired computer. It still works great and the internal components still have plenty of life left.

The downside of this PSU is that it is a group-regulated design, which introduces a few issues:

- It requires a dummy load in order to turn on
- It shuts itself off when it detects a large imbalance between the rails
- I later learned that the 3V3 rail is especially sensitive to this issue

I managed to counteract this issue by placing two dummy loads on the 5V rail, and applying an even higher load to the 5V rail whenever I was drawing significant power from the 3V3 or 12V rails.

Although this PSU is not ideal for a benchtop power supply conversion, it still serves the purpose of this project very well, which is to recycle and reuse components that would have otherwise become electronic waste.

Ideally, I would recommend using an independently regulated PSU because it makes assembly, stability, and future usage much easier.

<p align="center">
    <img src="images/cm-500-psu.jpeg" width="400"><br>
    <em>Cooler Master Elite 500W V2 Power Supply</em>
</p>

### Dummy Load

*Skip this section if the PSU is NOT a Group-Regulated ATX PSU.*

Group-regulated ATX PSUs are older power supply designs where the output voltages are regulated together instead of independently, meaning the rails affect each other.

Older computers mainly drew power from the 5V rail, so many older PSUs require a load on the 5V rail in order to properly power on.

For this build, I used a 10Ω power resistor connected between the 5V rail and GND as a dummy load.

I strongly recommend using a properly rated power resistor and NOT a regular 1/2W resistor, because it will burn.

(Don’t ask me how I know.)

<p align="center">
    <img src="images/dummy-load.png" width="350"><br>
    <em>10W 10Ω Power Resistor</em>
</p>

### Disassembly

First, I removed the power supply from its original casing.

<p align="center">
    <img src="images/psu-out-of-case.png" width="350"><br>
</p>

Then I cut off all of the connectors. I recommend keeping as much wire length as possible just in case it is needed later.

I also kept one of the Molex connectors for the fans.

<p align="center">
    <img src="images/cut-connectors.png" width="350"><br>
</p>

### Reusing the Original Wall Connector

For this project, I reused the original wall connector and switch because it already had 3 input filter capacitors connected to it.

These capacitors help reduce noise from the incoming AC power.

An optional IEC320 female connector can also be used, but I would recommend resoldering the capacitors onto the replacement connector.

I needed to cut and reconnect the wires on the connector in order to mount it into the new case.

<p align="center">
    <img src="images/wall-connector-switch.png" width="350"><br>
</p>

### Installing the Dummy Load

*Skip this step if the PSU does not require a dummy load.*

I soldered the dummy load across the 5V rail to make testing the PSU easier throughout the build process.

<p align="center">
    <img src="images/solder-dummy-load.png" width="350"><br>
</p>

Similarly, I shorted the green PS_ON wire to GND and soldered them together to make it easier to power the PSU on and off during testing.

<p align="center">
    <img src="images/solder-power-on-wire.png" width="350"><br>
</p>

### Mounting the PSU PCB

To mount the PSU PCB into the case, I drilled my own holes and used a soldering iron to install M3 brass inserts.

Originally, I tried designing the mounting holes directly into the 3D model, but it failed and I ended up drilling the holes manually anyway.

For Version 2 of the model, I removed all of the mounting holes entirely so builders can drill their own holes based on their specific PSU.

When drilling holes, I had to carefully consider component placement to avoid clearance issues.

Later in the build, I actually had to drill a second set of holes because the power connector was colliding with the PCB.

<p align="center">
  <img src="images/drill-hole.png" width="250">
  <img src="images/brass-insert.png" width="250">
  <img src="images/re-insert-holes.png" width="250">
</p>

### Installing the Wall Connector

To install the wall connector, I cut the wires connecting it to the PCB and used hot glue to secure it into the case.

<p align="center">
  <img src="images/install-wall-connector.png" width="350">
</p>

I then installed additional brass inserts to attach the bottom case to the front and back sections.

<p align="center">
  <img src="images/brass-insert-2.png" width="350">
</p>

### Installing Rear Components

I installed the remaining rear components using either nuts and bolts or hot glue, then mounted the rear case onto the bottom case using M3x8mm screws.

<p align="center">
  <img src="images/back-case.png" width="350">
</p>

After that, I reconnected the wall connector exactly the way it was originally wired.

This step was much harder than it looked.

<p align="center">
  <img src="images/reconnect-wall-connector.png" width="350">
</p>

### Initial Testing

After every major stage of the build, I tested the PSU to make sure everything was still working correctly.

I plugged in the fans and powered the unit back on.

All rails were outputting the correct voltages and the fans were running perfectly.

<p align="center">
  <img src="images/test-1.png" width="350">
</p>

### Front Panel Assembly

For my build, I designed the banana jack holes too small, so I had to drill them larger manually.

This issue was fixed in Version 2 of the model.

<p align="center">
  <img src="images/drilling-banana-jack.png" width="350">
</p>

I mounted all of the front panel components using hot glue along with nuts and bolts.

<p align="center">
  <img src="images/front-case.png" width="350">
</p>

### Power Rail Wiring

I joined all of the 3V3, 5V, and 12V wires together into their respective rails.

I tried to use as many wires as possible, but realistically only 2–3 wires are needed because this design will probably never draw more than around 10–15A per rail, which is already a lot of power.

Using fewer wires also made the crimp connectors easier to install and reduced cable clutter inside the case.

<p align="center">
  <img src="images/3V3.png" width="250">
  <img src="images/5V.png" width="250">
  <img src="images/12V1.png" width="250">
</p>

This PSU had two separate 12V rails, so I used the second rail to power the variable output through the ZK4KX/ZK5KX module.

<p align="center">
  <img src="images/12V2.png" width="350">
</p>

Final result with all crimp connectors installed:

I connected these wires to the fuse.

<p align="center">
  <img src="images/all-rails.png" width="350">
</p>

I also kept the remaining wires for connecting the fuse to the rocker switches.

<p align="center">
  <img src="images/cables-1.png" width="250">
  <img src="images/cables-2.png" width="250">
</p>

### Ammeter / Voltmeter Wiring

To power the ammeter and voltmeter modules, I joined all of their PWR and GND wires together and installed a crimp connector on them.

I powered them using the 12V rail from the Molex connector, connecting them in parallel with the fans.

This made the modules much easier to connect and disconnect throughout the build process.

I connected the red wire of the ammeter to the black banana jack.
I connected the black wire of the ammeter to GND.

<p align="center">
  <img src="images/ammeter-voltmeter.png" width="250">
  <img src="images/ammeter-1.png" width="250">
  <img src="images/ammeter-2.png" width="250">
</p>

### Output Wiring

I used additional wire length to create short jumper cables connecting the output switches to the red banana jacks.

<p align="center">
  <img src="images/short-cabes.png" width="350">
</p>

I connected the short cables from the switches to the red banana jacks.

<p align="center">
  <img src="images/connecting-1.png" width="350">
</p>

### LED

I soldered the respective resistors onto the LEDs' positive terminals and additional wire to their negative terminals before installing them.

LEDs are diodes, so polarity matters when installing them.

- The positive terminal is connected to the red banana jack
- The negative terminal is connected to the black banana jack

<p align="center">
  <img src="images/led.png" width="350">
</p>

### Common Ground

I crimped together 3 wires per rail for GND and connected them to the black banana jack.

<p align="center">
  <img src="images/ground-1.png" width="250">
  <img src="images/ground-2.png" width="250">
</p>


### Test

I tested the PSU again to make sure all rails, ammeters, and LEDs were functioning properly.

<p align="center">
  <img src="images/test-2.png" width="350">
</p>

### High Load Mode

To add a High Load feature to this build, I added a second 10W 10Ω power resistor in series with a switch, so whenever the switch is flipped, a higher load is applied to the 5V rail to balance the load.

The LED is connected in parallel with the resistor to indicate when High Load Mode is active.

<p align="center">
  <img src="images/dummy-load-2.png" width="250">
  <img src="images/high-load.png" width="250">
</p>

I installed both resistors using hot glue, which helps mount them to the case and provides some insulation.

<p align="center">
  <img src="images/resistors.png" width="350">
</p>

### Fans

The fans I used had mounting holes that were not flush on the intake side, so in the photo they were temporarily mounted as exhaust fans.

Later on, I used nuts and bolts to reinstall them properly as intake fans.

<p align="center">
  <img src="images/fans.png" width="350">
</p>

### Finalize

Some housekeeping items:

- Cut short and heat shrink all unused wires together
- Cut short, resolder, and heat shrink the PWR ON and GND wires
- Cable manage everything using zip ties
- Install the top case

<p align="center">
  <img src="images/cable-management.png" width="350">
</p>

---

# Bill of Materials

- [BOM](docs/bill-of-materials.pdf)

---

# Video

Coming Soon