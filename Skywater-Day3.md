# Spice simulation for circuit 


# 16-mask CMOS process
Step 1: Selecting the substrate.
- Type, resistivity, doping level, orientation.

Step 2: Create active region via isolation for transistors.
- Step a: Add base layers on top of substrate (SiO2, Si3N) and photoresist.
- Step b: Add mask and shine UV light on top of the mask that removes the exposed photoresist.
- Step c: Etech off exposed Si3N and after remove photoresist.
- Step d: Heat up in oxidation furance that grows the exposed SiO2 while other SiO2 are covered by Si3N. Process called Local Oxidation for silicon (LOCOS). Creates Isolation areas.
- Step e: Etch remaining Si3N.

Step 3: N-Well and P-Well Formation.
- Step a: Add photoresists and mask to specific locations.
-  Step b: Shine UV light and remove mask after.
-   Step c: Ion implantation of Boron to create p-well in P-substrate in the expose side with no photoresist.  ~ 200keV (damages Si02)
- Step d: repeat A-B on the p-well side.
- Step e: Add phosphorous for n-well.   ~200 kEV (damages Si02)
- Step f: Place in a high temperature furance to form deep N-well and P-well through diffusion of phosphrous and boron respectively.
  
Step 4: Formation of the gate
- Step a: Step 3a-3b and implant Boron to the p-well side at the surface of the substrate (under SiO2) with low energy ~60keV. Remove photoresist.
- Step b: Repeat for the n-well using Arsenic or Phosorous
- Step c: Use HF solution to etch damaged Si02 and regrown with high quality SiO2
- Step d: Add Polysilicion layer (Doped for phosphorous for low gate resistance) on top of newly formed SIO2
- Step e: Repeat 3a-3b to to create 2 pillars of photoresist above polysillicon layer in the n-well and p-well sections.
- Step f: Etch polysillicon not covered by photoresist and remove photoresist after. (The result should be a area of polysillicon above the SiO2 layer in both of the wells)

Step 5: Lighly dope drain (LDD) formation
- Step a: Repeat 3a-3b with the exposed side in the p_well and add phosorous to creata a lighly doped N- implant on the inside of the lighly doped p implant inside the p-well ionside hte p-substrate between both sides of the polysilicon strip in the p-well
- Step b: Repeat a but using Boron. Creating a P- implant.
- Step c: Create side-wall spaces using a thick layer of SIO3 or Si3N and etching down to the P- implant inside the P-substrate expect on the sides of the polysilicon strip.

Step 6: Source and drain formation
- Step a: Add small layer of screen oxide ontop of the p-implant/n-plant to prevent channling.
- Step b: Repeat step 3a-3b. Exposed side is the n-implant/p-well side. Turns the n- implants to a strong n+ implant. Remaining n-implant hides under the sidewall space near the polysilicon strip.
- Step c: Repeat but add Boron to the p-/n-well side creating a p+ implant. Same structure layout.
- Step d: Place in a high temperature furance to anneal (develop and diffuse).

Step 7: Step to form contact and interconnects (local)
- Step a: remove HF solution.
- Step b:Deposite titanium on wafer surface using sputtering.
- Step c: Heat in 600-700C in N2 for 60 sec to create TiSi2 (low resistanct; in contact with silicon when in oven)or TiN (used in local communication).
- Step d: Step 3a-3b (Specific locations ontop of the reacted TiN layer).
- Step e: Etch off exposed TiN to create specfic location communication using RCA cleaning. Remove photoresist after.

Step 8: Higher level metal formation:
- Step a: Add thick layer of SiO2
- Step b: Chemical Mechanical polishing (CMP) to make the SiO2 layer flat with no hill or bumps
- Step c: Step 3a-3b and etch exposed layers (thorugh SiO2) and remove photoresist after.
- Step d: Add a TiN (Good barrier between bottom interconnect and top interconnects.
- Step e: Add tungsten and use CMP to cut excess down.
- Step f: Add aluminum layer and repeat step 3a-3b down to the CMP level in step e. Remove photoresist (Aluminum is a on the SiO2 layer)
- Step g: Deposit more Sio2 and repeat step3a-3b to makes holes down to the aluminum.
- Step h: add TiN and tungsten on top of aluminum using step8a-8e
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
Step 3: Open the sky130_inv.mag file (the characterization of a inverter) using *magic -T sky130A.tech sky130_inv.mag*. You show see a k-map similar desgin: 
<img width="731" height="762" alt="image" src="https://github.com/user-attachments/assets/d984b19b-a0d8-4b39-a7dd-aaf10912b778" />
