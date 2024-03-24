## Introduction

RPWR is a spin-off of another experience called RBWR. If you are new to both experiences it is advised that you first try RBWR as it is a more complete game with much more support from the community and generally easier to comprehend.
RPWR is a simulator of a small modular PWR nuclear power plant. Only the control room is implemented at this time. The general idea of RPWR is to provide you with a realistic experience, including all main components interacting together like in real life, but without getting too much into details of every single switch of a real power plant.
It is advised that you begin with the startup guide (gear icon on the right) on a fresh private server, prefferably alone.
# Reactor Control

The reactor panel is located on the left side of the control room. It consists of the main panel and two supporting panels (CVCS and RHR).

## Reactor Panel

The reactor panel consists of the main reactor control switches (for the control rods) and secondary control switches (for the boric acid). The following switches are available:

On the left:
- ROD MOV (rod movement) - Allows to manually withdraw or insert the control rods.
- MOVE SPD (movement speed) - Allows to change how quickly rods move (slow/medium/fast).
- MODE SEL (mode selector) - Allows to pull all rods at once (ALL) or single, selectable groups of rods (GROUP).
- AUTO BLNC (automatic balancer) - Automatically balances power output between individual groups of rods.
- AUTO MODE (autocontrol mode) - Allows to choose whether autocontrol should use rods or boric acid injection.
- BORIC ACID (boric acid) - Allows to manually inject boric acid into the core or dilute with water.

On the middle:
The middle section allows you to select individual groups of rods or their banks. A 2-d diagram of the rod groups is provided although it is not realistic for a PWR plant, we decided to provide it so that the player knows  the exact position of any selected rod. Also whole banks (sets of 4 groups) can be selected. There is also a switch for startup and run mode.

On the right:
- ROD LEVEL - This is a selector and indicator for Vertical Rod Display. It is possible to see one of 10 vertical slices of the core, or power averaged throught all levels.
- IPR CTRL/LEVEL - This is a selector for the IPR mode (refer to startup).
- SETPOINT - Power setpoint selector for the autocontrol, there are also buttons for predefined powers.

## CVCS

On the left side of the reactor panel there is CVCS panel which is used to recycle used boric acid. The system consists of a water tank, boron concentrate tank, external tank and evaporator. Whenever water or boric acid is injected into the core, the same amount of water from the core is moved into the external tank. This water will consist of some boric acid (depending on concentration), which can be recycled.

- XFR EVAP (Transfer to evaporator) - Transfers water from the external tank into evaporator.
- EVAP HEAT (Evaporator heater) - Heats up the evaporator using live steam from the secondary system, water will boil in evaporator changing into steam, while the remaining boric acid will stay at the bottom.
- STEAM OUT - Relieves the steam from the evaporator to the condenser (not simulated) and back to water tank.
- CONC OUT - When all water is evaporated, moves remaining boric acid back to boric acid tank.

## RHR

Residual Heat Removal panel is on the far left side. At this time only RHR mode is simulated. RHR will cool down left/right parts of the core during shutdown if pressure is below 3MPa.
# Pressurizer

The pressurizer is a device used to maintain proper pressure in the primary circuit (usually between 10-15 MPa). In order to do so pressurizer is built as a tall vessel filled halfway with primary circuit water. Pressurizer heaters will heat this water allowing the water to boil and creating steam pressure which affects the whole primary system.
Pressure should always be enough that the water never boils in the primary circuit outside of the pressurizer. As such the boiling temperature should always be higher than primary water temperature.

The primary circuit consists of two legs, one for the left side of the reactor, the other one for the right. The pressurizer is located in the left leg. There are several devices in the pressurizer:

- 4 Pressurizer heaters designed to heat water in the pressurizer and raise pressure via boiling.
- Makeup/drain to change water level in the pressurizer.
- 4 Relief valves to dump steam and lower pressure in emergencies.
- 2 Pressurizer sprays to cool down the steam by spraying cold water in it.

The pressurizer is also equipped with a very strong startup heater. As some PWRs can startup solely on decay heat, we have provided the startup heater to make the startup process quicker. It will heat the left leg of the primary circuit.
# Reactor Cooling

This is the main panel for the primary cooling circuit. Reactor Coolant Pumps will circulate water between the core and the steam generators, transfering heat between the primary (tube) side and the secondary (shell) side.
There are two legs in the system (left leg leading to left SG and right one leading to right SG), each having 2 pumps (RCP1 and RCP3 for the left leg, RCP2, RCP4 for the right leg).
Each leg of the system is divided into 2 parts, the hot leg (between the core and SG) and the cold leg (between SG and the core, where RCPs are located).

The right part of the panel has the autocontrol, which allows you to maintain a predefined hot leg temperature in each side (left/right).

Some PWRs rely on constant RPM pumps, where the temperature in the core depends on reactor power (the higher power, the higher temperature). We decided to implement variable RPM pumps which allow to keep constant temperature in the core as this is generally more efficient and allows you to experiment on how systems interact between each other.
# Feedwater/SG panel

This panel is the main control panel for the secondary system. It consists of 2 steam generators and 4 pumps. Each steam generator has an auxiliary electrically driven feedwater pump and a steam driven feedwater pump. The main goal of this panel is to maintain proper water level in the steam generators by adjusting feedwater flow to them. Autocontrol is provided which can maintain a desired setpoint with a selected pump (electrical or steam driven).
Electrical pumps should be used during startup, emergencies and as a support for full power operations. During normal operations steam driven pumps should be used (if enough steam is provided).
There are 4 relief valves which allow to dump steam and pressure in emergencies. Also the Main Steam Isolation Valve (MSIV) is located on the panel. This valve isolates the system if not enough vacuum is available in the condenser (above 500 mbar).
Additional makeup and drain valves are provided for the hotwell and also a CST makeup pump.
# Turbine panel

The turbine panel consists of two main valves. The bypass valve and turbine valve. They can be used when MSIV is open. Bypass is used to move steam directly into the condenser bypassing the turbine, on the other hand the turbine valve directs steam into the turbine.
The turbine can be started when enough vacuum is available in the condenser (50-70mbar) and optimal pressure (around 7100 kPa) is available in the main steam line. An automatic runup system is available which automatically controls both the bypass and turbine valves as well as allowing you to change the target RPM and runup speed. Synchronization speed is 1500 RPM.
In order to synchronize the generator, the exciter should be enabled and adjusted to around 6600V. The turbine should be a little above 1500 RPM, with the synchroscope pointing top and slowly moving clockwise. At this moment the generator breaker should be closed. If synchronization was successful the auto pressure hold can be enabled which will keep desired pressure automatically.
# Condenser

The condenser uses an external water source to cool down the steam and let it condense back into water, which gathers in the hotwell. The condenser has several devices:

- 2 CARs (Condenser Air Removal), which are electric pumps which initially lower condenser pressure to allow MSIV to be opened.
- 4 SJAE (Steam Jet Air Ejectors) which are used to eject uncondensable gasses from the condenser. Two of them should always be on when steam is available.
- 2 Circulation pumps that circulate external water to cool down the steam. The more steam inflow, the more flow is required. Autocontrol is provided to keep condenser vacuum at desired level (55mbar).
  # Water treatment

This small panel consists of:

- 2 Polishers that demineralize and clean the feedwater, only one should be active at all times.
- 4 Pre-heaters which are used to heat up the feedwater for higher efficiency, they should be all active when steam is available.

# Electrical

The electrical panel is used to control breakers that power all devices in the plant.

## Offsite Lines

There are two offsite lines available:
- Line 911 - this line can be used to power the plant during startup and to send energy to the grid to meet demand.
- Line 826 - this line can be used only as auxiliary for startup and during outages on Line 911, it won't accept power.

## Buses

There are 3 buses:

- Main Bus, powers non critical equipment.
- Safety Bus, powers critical equipment.

Both of these buses can be connected either to one of the offsites or the generator. Safety bus can also be powered by diesel generator.

- Low Power Bus, powers devices such as lights, controls or ventilation.

This bus is powered from the Safety Bus or a battery

## Islanding mode

Islanding is a mode in which the plant powers itself. In order to go into islanding mode, the power production must be exactly matched with site power demand. Next Line 826 breaker should be opened. The turbine will desync but will still provide power to the buses. Depending on load changes RPM might change and it must be kept between 1450-1550. Whenever Line 826 is reconnected, the generator will have to be synced to it again.
# Master-Slave concept 

PWR plants have some interesting effects and feedback loops, lets summarize them here:

## Reactor feedback

In a light water moderated reactor, the reactivity will depend on density of the water coolant. Therefore the higher the temperature in the core, the lower the reactivity. This natural phenomenon is main safety effect which stabilises the core. If the power raises and core temperature raises, the reactivity will drop. On the other hand when power and temperature drop, the reactivity will raise. The reactor is therefore stable although it will tend to oscillate around optimal power like a pendulum.

## Primary circulation feedback

As the flow in the primary system can be controlled, temperature of the core can be changed by just adjusting the RCPs. When the flow is higher, more cooling is provided and core temerature will drop. Reactor will feel this effect and will automatically raise power to reach previous temperature. Of course it works the same way in the other direction. If we reduce cooling, temperature will raise, reactivity will drop, again reducing temperature.

Contrary to popular belief, primary circuit flow alone can't be used to change reactor temperature in the long term as reactor will always react to the change. It can be however another mean to change the reactor power. If more cooling is provided the reactor power would rise.

## Secondary circuit feedback

The secondary circuit takes power from the primary. The more flow in the primary and the higher the primary temperature, the more steam production one can expect. However the temperature in the secondary is mostly set by the pressure which affects boiling point. In other words the higher the pressure, the higher the water temperature will rise before it boils. As the secondary temperature affects heat exchange, pressure changes can affect the whole process. This is where Master/Slave concept arises.

## Turbine-Master/Reactor-Slave

While you might think that the logical way to operate the plant is to first set power of the reactor for a demand and then adjust all other systems to deal with this power it is not how a PWR works. In a BWR reactor the scheme would be exactly like that and we suggest training this concept in RBWR first. In a PWR reactor the concept is reversed:

- Power output should be set by steam demand in the secondary first, and rest of the systems should self adjust.

Let's discuss how this works. Let's assume we have a reactor in a stable state with everything setup for a certain power production in the turbine. Now lets open the turbine valve more, requesting more steam and power. What happens?

As more steam is used in the secondary pressure will drop. This will lower the boiling point causing temperature in the secondary to drop. How will primary react? With lowering water temperature in the steam generators, the water in primary will be cooled more effectively. In other words more power will be given away. The temperature difference between hot and cold legs will rise and this is the direct indication of power exchange between systems. Cooler water will enter the core.

How will the reactor react? With cooler water entering the core reactivity will raise. As the power rises, the hot leg will get hotter than before raising also the temperature in the cold leg. This will inevitably cause more steam generation in the secondary and the pressure would raise back. We can expect a new steady state which will cause the pressure to come back to previous value with just more steam flow and more power generation. Of course all systems would react similarily when demand is lowered.

## The pendulum

This is the theory. We should adjust steam demand and hope for all other systems to adjust. However in reality the systems work a bit like a pendulum. If you change the state of balance, the pendulum will move in that direction, but won't stop there. It will overshoot and then swing back. Therefore even though we might have the correct steady state parameters for our new demand, all systems will swing forth and back. Reactivity will raise, temperature will raise, pressure will raise, this will raise temperature in the cold leg, which will kill reactivity, so temperature will drop same as steam generation etc.

Therefore operators will try to dampen these oscillation by for example artificially lowering reactivity when the reactor is about to shoot over it's steady state power, and then bring it back so it doesn't swing back. Manual operation of a PWR is much more difficult than a BWR because so many things depend on each other. To make it even worse if one decides to enforce some parameters with autocontrol, the whole system may react differently than expected.
# Basic Interactions

Assuming that you are operating the reactor manually you should consider the following interactions between systems:

# Changing reactor power

Raising reactor power will cause primary temperature to rise and will yield higher steam production. Lowering the reactor power will have a reverse effect.

# Changing primary flow

Raising primary cooling flow WILL NOT change the temperature in the primary. Instead reactor will react with higher power to more or less maintain the temperature. Therefore:
- RCP flow can be treated as another means of changing the reactor power (along with rods and boric acid). More flow will cause more power and more steam production.
- In order to reduce primary temperature after cooling flow is raised, reactivity must be reduced with other reactor controls to stop the power raise.

# Changing steam demand

Opening the turbine valve more, will cause pressure to drop and reactor power to raise to meet a higher steam demand. Feedwater temperature after an initial drop will raise back again.
