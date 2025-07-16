How the chip works: C Language → Compiler → Assembly language (RISC\_V assembly language) → Computer code (1s and 0s) → Output

Going from assembly language architecture to something the hardware can understand: Assembly language has specific layout unique for different types of chips. Implementation of specific design of the assembly language to the specific design of the chip using Register-transfer level abstraction (RTL) in Hardware description languages (HDL), like Verilog, and synthesize the design into a file format of gates that can be made into a chip specific for the design of the assembly language 
- Intel Chips: x86/x64/x32 architectures  
- RISC-V architectures used for specific chips that can understand RISC-V  

Full openlane ASIC flow chart. Note: OpenLane is fully automated and can require no human input. The only required files are the RTL desgin files and the configuration files of your specific chip desgin. Openlane will handle the rest and convert the RTL files into a GDSII file, which can be sent into a foundry and allow your chip to be manufactured. Later on, I will describe where you can see the results, logs, and tests of each flow and how to make modification to the flow using configuration files.   There is a possibility for interactive mode with commands to control the ASIC design flow and allows you to see the results and outputs of each section before moving on to the next section.
<img width="1787" height="781" alt="Screenshot 2025-07-16 001314" src="https://github.com/user-attachments/assets/c81f4e7c-0d62-4496-ae86-31013bf76fcf" />

Setting up openlane after using booting up the virutal machine with openlane and linux installed on it.
Step 1: Head to where the openlane directory is stored at in commond prompt by using *cd <file-path>* (the navigation command of your linux os)
      --> Step 1.5: If you want to learn more about how openlane works and what files it pulls from, explore the pdk file in the openlane_working_dir or where you pdk files are stored and explore the desgins and the technology specific of the desings you are using or see all the designs your PDK can offer. 
Step 2: Open the isolated working enviorment by typing *docker* in command line after you are in the openlane directory. (You should see the command line turn into bash-4.2$), then run *./flow.tcl -interactive* to run openlane interactivly and in an isolated interactive format. 
      --> step 2.5: If you want openlane to complete everything for you (turning you're RTL files into GDSII files) without having to run the commands indiviudally, run *./flow.tcl -desgin <design_name>*. The design has to be in a specific location for openlane to recongize it. Please check the openlane documentation if you are doing it through this method. 
Step 3: Setup the file system specific to the flow that openlane requires by using *package require openlane 0.9* and running *prep -desgin <desgin-name>* afterwards. Note: if you have a previous design that you want to contiune to work on, add the modifier *-tag <run-name> (usually the date and time) after the design name modifier.* For more infomration on seting up the file system, refer to the docs through this link: [https://armleo-openlane.readthedocs.io/en/latest/docs/source/openlane_commands.html)
      --> After the preparation step, if you go to PATH-TO-YOUR-OPENLANE-DIR/openlane/designs/NAME-OF-YOUR-DESIGN/runs/DATE+TIME-OF-YOUR-RUN, you can see where all the information of your desgins are stored (use ls -lrth, another linux command). You can see the results of each step in the results directory. You can see how your chip function in the report directory. You can see all the configuration of your chips in config.tcl and you can see the command inputs in the logs directory.  <img width="658" height="157" alt="Screenshot 2025-07-16 153224" src="https://github.com/user-attachments/assets/6e2f3cfe-13c5-4a4c-9a2d-c1b5651667e6" />
Step 4: The last step day 1 is going to touch on is the *run_synthesis* command where the first step of turn your RTL to a GDSII file get runed, (refered to the ASIC desgin flow above). This step takes a few minuntes and you should be able to see the results in the results/synthesis dir.  




Useful resources to learn more:
[https://www.youtube.com/live/EczW2IWdnOM?si=5d2mLJYNQx8F5o8u](https://www.youtube.com/live/EczW2IWdnOM?si=5d2mLJYNQx8F5o8u)   
[https://www.youtube.com/live/Vhyv0eq\_mLU?si=T1sAK3iZwZYvOXp7](https://www.youtube.com/live/Vhyv0eq_mLU?si=T1sAK3iZwZYvOXp7) 
[https://armleo-openlane.readthedocs.io/en/latest/index.html)




