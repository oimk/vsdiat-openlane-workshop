# Spice simulation for circuit 
In the previous day, we went over the theory on how to simulate the voltage transfer characteristics (VTC) in a hypotheical component. In this day, we are trying to do the same thing in realtime through spice simulations. But to do that we have to define the circuit first using the SPICE deck. 

## Spice Deck
Spice decks explain everything about the Spice deck. One of the descriptions is the component connectivity, which describes how different components like the PMOS and NMOS connect to each other, to VDD, to VSS. 

<img width="301" height="389" alt="image" src="https://github.com/user-attachments/assets/453e174b-e09a-407c-964c-68c4cbc54018"/><figcaption>Image from VSDIAT course & taken from lecture. </figcaption>


We also need to define the Component values, which describes the dimensions of a component. Below, both the PMOS and the NMOS have a channel width of 0.375 micron and a channel length of 0.25 micron. Ideally, the PMOS should have bigger values compared to the NMOS. Futher, we also define the voltage values of the gate and drain, which are 2.5V respectively.
<img width="864" height="729" alt="image" src="https://github.com/user-attachments/assets/571d049e-6914-47c9-8ce2-a8c655ed8420" /><figcaption>Image from VSDIAT course & taken from lecture.</figcaption>

In the Spice deck, we must define the nodes too. Nodes are two points where a component lies in between. Below, all the components lie between two nodes.
<img width="406" height="363" alt="image" src="https://github.com/user-attachments/assets/75079b27-66dc-441a-b387-656abafea3f1" /><figcaption>Image from VSDIAT course & taken from lecture.</figcaption>

Now we can start writing the Spice deck. The Spice deck describes the circuit. We write the connectivity, dimensions, component values of of each component into the file. Below, M1 and M2 are the names of the PMOS and NMOS respectively and the files describes the connectivity, type, and dimensions. Cload is the name of the output load capacitor and the file describes it's capacitance. Vdd and Vin are the name of the source and the drain and the file desribes it's connectivity and voltage. Then, we have the simulation commands. The file tells the input voltage, (Vin) to increase from 0 to 2.5 voltages with a rate of 0.05 volts. The last thing is to include the technological parameters of the specific compoment like the PMOS and the NMOS. 
<img width="874" height="459" alt="image" src="https://github.com/user-attachments/assets/976db9f3-5c6e-4127-b1a3-d157049589e8"/><figcaption>Image from VSDIAT course & taken from lecture.</figcaption>

## Spice Simulation
To run the simulation you must: 
1. Go to the file path where the souce file are stored using the cd command in the spice terminal
2. Source the file and run it.
3. Run set point and choose the right plot (DC transfer characteristics)
4. Then run plot out vvs in

By simulating differnet ratios for the dimension of the NMOS and PMOS, we achive the same shape but a different phase. Below, it is important to note the switching threshold, which is where Vin = Vout. For the left one, it switches at a voltage of 1, while for the right it switches at a voltage of 1.25. It is important to note that the dimensions of the channel in the MOSFETs are differnet in the left graph and the right graph. This means that the robustness these two differnet circuit with the variation in the ratio between the PMOS and the NMOS causes this differnet. 
<img width="1900" height="919" alt="image" src="https://github.com/user-attachments/assets/680c1572-4659-4b5c-8449-2a67adccc977" /><figcaption>Image from VSDIAT course & taken from lecture.</figcaption>

To do a transient analysis, instead of applying a constant voltage, we input a pulse voltage in the Spice file for Vin. Below, the graph the x axis is the time in ns, and the y axis is the voltage. To caculate the progation delay, compare the rise and fall time in the switching threshold when vin is falling and vout is rising and when vout is falling and vin is rising.
<img width="543" height="419" alt="image" src="https://github.com/user-attachments/assets/985d4d48-3cd2-4061-a333-8a9897dd3a88" /><figcaption>Image from VSDIAT course & taken from lecture.</figcaption>


   



# 16-mask CMOS process
Step 1: Selecting the substrate. Use a low doping level. 
- Type, resistivity, doping level, orientation.
- <img width="789" height="280" alt="image" src="https://github.com/user-attachments/assets/1d092bb2-6c52-4621-b657-02f17db22aea"/><figcaption>Image from VSDIAT course & taken from lecture.</figcaption>

Step 2: Create active region via isolation for transistors. (1 mask used)
- Step a: Add base layers on top of substrate (SiO2, Si3N4) and photoresist.
- Step b: Add mask and shine UV light on top of the mask that removes the exposed photoresist.
- Step c: Etech off exposed Si3N and after remove photoresist.
- Step d: Heat up in oxidation furance that grows the exposed SiO2 while other SiO2 are covered by Si3N. Process called Local Oxidation for silicon (LOCOS). Creates isolation regions.
- Step e: Remove remaining Si3N4 using phosphoric acid.
<img width="1897" height="774" alt="image" src="https://github.com/user-attachments/assets/beaea84f-cc42-4656-b4c1-efe765fc66cc" /><figcaption>Image from VSDIAT course & taken from lecture.</figcaption>

Step 3: N-Well and P-Well Formation. (2 Mask Used)
- Step a: Add photoresists and mask to specific locations.
-  Step b: Shine UV light and remove mask after.
-   Step c: Ion implantation of Boron to create p-well in P-substrate in the expose side with no photoresist.  ~ 200keV (damages SiO2)
- Step d: repeat A-B on the p-well side.
- Step e: Add phosphorous to make n-well. ~200 kEV (damages SiO2)
- Step f: Place in a high temperature furance to form deep N-well and P-well through diffusion of phosphrous and boron respectively.
<img width="839" height="356" alt="image" src="https://github.com/user-attachments/assets/c537d0f2-403b-4eea-9b1d-6232ea4c6f24"/><figcaption>Image from VSDIAT course & taken from lecture.</figcaption>

  
Step 4: Formation of the gate (3 Mask Used)
- Step a: Step 3a-3b and implant Boron to the p-well side at the surface of the substrate (under SiO2) with low energy ~60keV. Remove photoresist.
- Step b: Repeat step a for the n-well using Arsenic or Phosorous
- Step c: Use HF solution to etch damaged Si02 and regrown with high quality SiO2
- Step d: Add Polysilicion layer (Doped for phosphorous for low gate resistance) on top of newly formed SIO2
- Step e: Repeat 3a-3b to to create 2 pillars of photoresist above polysillicon layer in the n-well and p-well sections.
- Step f: Etch polysillicon not covered by photoresist and remove photoresist after.(The result should be a area of polysillicon above the SiO2 layer in both of the wells)

<img width="694" height="315" alt="image" src="https://github.com/user-attachments/assets/ece8ddfb-9481-4259-a4e0-68ad42177f52"/><figcaption>Image from VSDIAT course & taken from lecture.</figcaption>


Step 5: Lighly dope drain (LDD) formation (2 Mask Used)
- Step a: Repeat 3a-3b with the exposed side in the p_well and add phosorous to creata a lighly doped N- implant on the inside of the lighly doped p implant.
- Step b: Repeat a but using Boron, creating a P- implant inside the lightly doped N implant. 
- Step c: Create side-wall spaces using a thick layer of SIO3 or Si3N and etching down to the P- implant inside the P-substrate expect on the sides of the polysilicon strip.
<img width="779" height="365" alt="image" src="https://github.com/user-attachments/assets/f8159206-e91e-4e1b-9c78-32597c5db039"/><figcaption>Image from VSDIAT course & taken from lecture.</figcaption>


Step 6: Source and drain formation (2 mask)
- Step a: Add small layer of screen oxide ontop of the p-implant/n-plant to prevent channling.
- Step b: Repeat step 3a-3b. Exposed side is the n-implant/p-well side. Turns the n- implants to a strong n+ implant. Remaining n-implant hides under the sidewall space near the polysilicon strip.
- Step c: Repeat but add Boron to the p-/n-well side creating a p+ implant. Same structure layout.
- Step d: Place in a high temperature furance to anneal (develop and diffuse).
<img width="691" height="324" alt="image" src="https://github.com/user-attachments/assets/8d22f9e6-83c8-4706-84b4-dc7c2d9e4fdd"/><figcaption>Image from VSDIAT course & taken from lecture.</figcaption>


Step 7: Step to form contact and interconnects (local) (1 mask used)
- Step a: Remove oxide using HF solution.
- Step b: Deposite titanium on wafer surface using sputtering.
- Step c: Heat in 600-700C in nitrogen gas for 60 sec to create TiSi2 (low resistanct; in contact with silicon when in oven)or TiN (used in local communication).
- Step d: Step 3a-3b (Specific locations ontop of the reacted TiN layer).
- Step e: Etch off exposed TiN to create specfic location communication using RCA cleaning. Remove photoresist after.
<img width="725" height="343" alt="image" src="https://github.com/user-attachments/assets/be3c4411-b8a1-4f2a-885a-adab19077199"/><figcaption>Image from VSDIAT course & taken from lecture.</figcaption>


Step 8: Higher level metal formation: (5 mask used)
- Step a: Add thick layer of SiO2
- Step b: Chemical Mechanical polishing (CMP) to make the SiO2 layer flat with no hill or bumps
- Step c: Step 3a-3b and etch exposed layers (thorugh SiO2) and remove photoresist after.
- Step d: Add a TiN (Good barrier between bottom interconnect and top interconnects.
- Step e: Add tungsten and use CMP to cut excess down.
- Step f: Add aluminum layer and repeat step 3a-3b down to the CMP level in step e. Remove photoresist (Aluminum is a on the SiO2 layer)
- Step g: Deposit more Sio2 and repeat step3a-3b to makes holes down to the aluminum.
- Step h: add TiN and tungsten on top of aluminum using step 8d-8e
- Step i: Add aluminum layer on top and use step3a-3b to make a hole down to the second SI02 layer with aluminum on top at specifc locations
- Step k: Add top dielectic to protect your chip;
- Step z: Use the final mask to crete ports to interface with the electrical components.


Final picture of the CMOS:
<img width="1409" height="983" alt="image" src="https://github.com/user-attachments/assets/3558fb23-0af0-4594-a32f-c63503e6a0ac" /><figcaption>Image from VSDIAT course & taken from lecture. Wood = SI02. Pink = aluminum. Blue with dots = tungsten. Lightblue = TIN. Red = polysilicion. Dark blue = Titanium. Green = Si3N4 or Sio2 </figcaption>


  
  
  

# Changing/Revising in openlane
If you ever made and mistake in openlane or wish to change anything, Openlane allows you to go back and change the necessary config files and run the flow from the point where the change took place. To do this, you have to modify the specific config files where you want to changes to happen. Re-Run the flow or the specific command that your changes affect (For Example: IO placer are placed in the floorplan step so if you want to moddify the IO placers, you have to go to the floorplan.tcl file location in the ../openlane/configuration folder, find FO_IO_MODE (the variable that controls IO placement), copy it full name and run *set ::env(FP_IO_MODE) number* (in our case it's 2) in the openlane interactive docker, and then run *run floorplan*.) To see your changes, do the magic -T command found in Day 2. In our case, changes made to the IO look like this:
<img width="656" height="633" alt="image" src="https://github.com/user-attachments/assets/090d1a83-34b6-4176-878a-2f94cab411dc" />

# Day 3 Commands 
Step 1: Copy this github repository https://github.com/nickson-jose/vsdstdcelldesign.git using *git clone* command. This repository contains a inverter magic file desgin.
Step 2: Copy the sky130A.tech file (path shown when using magic _T) into the new file that was clone on the computer.
<img width="739" height="186" alt="image" src="https://github.com/user-attachments/assets/85133195-2b16-4597-a1fc-be1bcb1c43ca" />
Step 3: Open the sky130_inv.mag file (the characterization of a inverter) using *magic -T sky130A.tech sky130_inv.mag*. You should see the following
<img width="731" height="762" alt="image" src="https://github.com/user-attachments/assets/d984b19b-a0d8-4b39-a7dd-aaf10912b778" />
Step 4: Select on different parts of the desgin of the inveter using the keypress s and use the *what* command in the terminal to determine what each part is. 

To add layers, select the part you want to add the layer to, move you're mosue to the layer type on the right, and then press the middle mouse button.

## Spice extraction to netlist
Step 1: Run *extract all* (To view the file location, type *pwd* and follow that path on the main terminal)   
Step 2: Run *ext2spice Cthresh 0 Rthresh 0*   
Step 3: Run *ext2spice*   
Step 4: Go to where the file was created (view step 1) and run *nano sky130_inv.ext*    
Step 5: To do transient analysis, we must add the dependicies files, power. ground and a pulse supply voltage. Add *.include ./libs/nshort.lib* and *./libs/pshort.lib* near *.option ...* and add *VDD VPWR 0 3.3V*, *VSS VGND 0.0V*, *Va A VGND PULSE(0V 3.3V 0 0.1ns 2ns 4ns)* in between *.subckt ... .ends* and *.trans 1n 20n* before *.end*   
Step 6: Change *.end* to *//.end* and add the following:   
 *.control*    
 *run*   
 *.endc*   
 *.end*   
<img width="878" height="598" alt="image" src="https://github.com/user-attachments/assets/cdc5f3db-ba03-43a2-b1df-a91ea89bc2c9" />
Step 7: Run *ngspice sky130_inv.spice*
<img width="744" height="773" alt="image" src="https://github.com/user-attachments/assets/2e21d533-01a7-44bd-baa3-868af31bb041" />
Step 8: Caculate the rise/fall delay and the rise/fall transition delay (day 2) by zooming in using the right and left mouse button. 

# Magic DRC Engine Excercise:
Basics of using magic and documentation can be found here: http://opencircuitdesign.com/magic/ 
To find more information about the Google Skywater 130nm process and the PDk itself, information can be found in this link: https://skywater-pdk.readthedocs.io/en/main/
To download this lab excercise, download the file in this link inside linux and extract the file. http://opencircuitdesign.com/open_pdks/archive/drc_tests.tgz

To start (inside drc_test directory):
Step 1: Open the met3.mag file using magic. Make a box under the big Met3 correct by design m3.4 adn run *paint m3contact*. Then run *cif see VIA2*. The output should look like this.
<img width="386" height="478" alt="image" src="https://github.com/user-attachments/assets/4ee727fd-f3e0-4111-be76-44c6fbf860a0" />
Step 2: Load poly.mag. In poly.9, here is a rule violation that is not flagged by the magic tool. The spacing between the two polyres is smaller than 0.48 micron. You can check by using the *box* command in the terminal. 
<img width="324" height="396" alt="image" src="https://github.com/user-attachments/assets/a858ccdf-736a-4572-a9ec-15c3fdb21ddf" />
This can be changing using through this: 
<img width="514" height="90" alt="image" src="https://github.com/user-attachments/assets/fcae4ed1-281a-4176-9831-c2f5b7216367" />
<img width="681" height="147" alt="image" src="https://github.com/user-attachments/assets/90787248-5127-468b-ac67-1698d47a3dc4" />
Step 3: Reload the tech file using *tech load sky130A.tech* and *drc check*. Then if you run drc check you should see an error.







