# MAJOR-PROJECT

Hello, my name is Mohammad Yaseen, and I am a student at Muffakham Jah College of Engineering and Technology studying Electronics and Communication Engineering.I have created this repository on 02-11-2021.

This repository is about my B.E. final year Major Project.

So here, I've shown how to use Iverilog and Gtkwave with VScode as an IDE to verify and simulate verilog modules.
As we all know, iverilog and gtkwave are opensource EDA tools that can only be run from a command prompt.To make things easier, I'm using vscode, which provides a compact view for dealing with Opensource tools.

Please install the following before proceeding:

1.icarus verilog (download link: https://bleyer.org/icarus/ for Windows).

2.VScode download link - https://code.visualstudio.com/download (also extentions i.Verilog-HDL/SystemVerilog/Bluespec SystemVerilog and ii.Graphviz Preview).

**We're ready to begin**

**Step-1**

I've opened the vscode and clicked on openfolder,it can be done in two methods as shown.


![1](https://user-images.githubusercontent.com/48184231/139592710-88827e56-72da-4875-84d9-8ec65815bee3.png)

![2](https://user-images.githubusercontent.com/48184231/139592765-a0930fff-b6a8-4f23-a3bc-04453641386f.png)


**Step-2**
Created a New Folder as shown. I named mine mux.
![image](https://user-images.githubusercontent.com/93651596/140561318-cf0f8e86-0813-42a7-b222-81aa7b3b189b.png)

**Step-3**

Created a new file with .v extension i.e., mux2x1.v by clicking on the button shown.
![image](https://user-images.githubusercontent.com/93651596/140562692-7a6b8ce2-c404-4649-972a-6ff8a2aaf5da.png)


I've written my verilog code in the created file
![image](https://user-images.githubusercontent.com/93651596/140562911-3e69570c-d197-4447-a2cf-15f83c8f12e6.png)

**Step-4**
Create a TestBench file for the written verilog module. the main key point to take care while writing testbench is as follows

1.include "$dumpfile"

2.include "$monitor"
![image](https://user-images.githubusercontent.com/93651596/140562048-b5d74f8a-c933-4370-9091-bdbaa3ec5822.png)

![image](https://user-images.githubusercontent.com/93651596/140562141-7abd325c-e8ba-4411-b9c6-16c5f9be3917.png)




**STEP-5** Now open a new terminal as shown and In terminal type the following commands

![7](https://user-images.githubusercontent.com/84916459/140509915-22a191af-1030-40c7-925a-1a90f6df643b.png)

COMMANDS

1.iverilog modulename testbenchname (in my case => iverilog .\mux2x1.v .\tb_mux.v) then press enter.

![8](https://user-images.githubusercontent.com/84916459/140509961-2b7a47a7-1de9-4afe-995e-a53781446b73.png)

**STEP-6**

2.vvp a.out

![9](https://user-images.githubusercontent.com/84916459/140510003-6a29b7fa-88b8-4e18-9619-e6fb1a96bf32.png)

you will be able to see resut in terminal as well as a new file with .vcd extention which is further use for generating waveforms

![10](https://user-images.githubusercontent.com/84916459/140510036-911b9117-8b3f-4de1-b936-024555bd18d5.png)

**STEP-7** :-for generating waveforms we are using gtkwave EDA Tool for waveform representation. use the following command for opening .vcd file in gtkwave

![11](https://user-images.githubusercontent.com/84916459/140510093-886e747c-ff12-4b26-a743-b4ab92df5ced.png)

3.gtkwave modulename.vcd in my case => gtkwave mux2x1.vcd


the following window pop's up click the testbench as shown and append ports.after that click zoom fit butten to observe all changing waveforms in a single window use mouse and click on the various points on waves to observe the values on left signals window.
![12](https://user-images.githubusercontent.com/84916459/140510111-57af7337-8e49-4532-a685-c7ee132c06bd.png)
![13](https://user-images.githubusercontent.com/84916459/140510295-0e2ce87e-763a-4d39-ae43-374a1ac707bc.png)
![![14](https://user-images.githubusercontent.com/84916459/140510185-9e12bf8a-22fd-4dba-9307-95472bcb2e1d.png)
![15](https://user-images.githubusercontent.com/84916459/140510317-06a6fbb2-4298-4af4-bc71-15397d5d38e6.png)

FOR THE SYNTHESYS PROCESS

The main tool which we are using for now for synthesys process is YOSYS(Download link:http://www.clifford.at/yosys/download.html )

In this synthesys process we are using SKY130 liberary File. all the required files will be provided .
![image](https://user-images.githubusercontent.com/93651596/140564257-795ded2a-02a6-400e-b102-674b446365a0.png)
![image](https://user-images.githubusercontent.com/93651596/140564318-ba681ef9-6468-4471-8d4b-9f0c39d8e722.png)
![image](https://user-images.githubusercontent.com/93651596/140564384-bc221f77-07fe-4269-8ccd-9b51b1431c80.png)




**STEP-1**

In terminal Type yosys to open yosys tool

![19](https://user-images.githubusercontent.com/84916459/140510389-3364006e-3406-4f9e-9500-0e9f1ee369e6.png)

**STEP-2**

then follow the next command Type: read_liberty -lib sky130_fd_sc_hd__tt_025C_1v80.lib

![20](https://user-images.githubusercontent.com/84916459/140510519-b11ac485-f83b-4cd7-ac47-03452cf3a92f.png)

**STEP-3**

after that type : read_verilog mux2x1.v // this command is use for reading module wirtten in verilog

![21](https://user-images.githubusercontent.com/84916459/140510540-6ee2b6a5-97e1-4d21-bfce-81ace953c715.png)

**STEP-4**

after that use syntax for synthesys process : synth -top modulename // modulename means the name given in the main verilog code file for example "module modulename(i,o)"

![22](https://user-images.githubusercontent.com/84916459/140510552-22c1fb7f-9898-4058-a44d-721654dc6049.png)

**STEP-5**

For mapping flip-flops to library use following command : dfflibmap -liberty sky130_fd_sc_hd__tt_025C_1v80.lib

![23](https://user-images.githubusercontent.com/84916459/140510586-8650d19e-79e8-4153-aabb-8e2f10f707f3.png)

**STEP-6**

For mapping logic to library file use following command : abc -liberty sky130_fd_sc_hd__tt_025C_1v80.lib

![24](https://user-images.githubusercontent.com/84916459/140510609-c073332a-9aaa-4bc2-9748-45ac8f2e844e.png)

**STEP-7**

for downloading netlist file type : show

![25](https://user-images.githubusercontent.com/84916459/140510650-f33e0c62-f8cc-4f5c-a63b-e4d467750188.png)
![26](https://user-images.githubusercontent.com/84916459/140510700-15e5a171-ce77-4cbb-ae35-ae86f5bfa9bb.png)

**STEP-8**

now use following command : tee -o report.txt stat -liberty sky130_fd_sc_hd__tt_025C_1v80.lib

![27](https://user-images.githubusercontent.com/84916459/140510726-269ea10f-4a05-40fc-82f7-5c856f2cf413.png)

**STEP-9**

we are done with synthesys now we need to download or write the synthesys file into some sort of file mainly in verilog formate for this use : write_verilog -noattr netlist.v

![29](https://user-images.githubusercontent.com/84916459/140510820-fc4a2b09-958d-4758-8b5e-a5b80d455925.png)

**Step-10**

now we can exit from yosys tool for that simply type "exit" and hit enter button.

![31](https://user-images.githubusercontent.com/84916459/140510875-a38bd9a1-4b6b-4f2c-8e50-c0847b341bb6.png)

Here report.txt file shows the statistical data of the design made 

![28](https://user-images.githubusercontent.com/84916459/140510939-8dc0145f-3c11-46cb-9353-b8a228876885.png)

and netlist.v file shows the all the detailed information which requred to make a intigrated Circuit. This is the file we give to foundry for making a physical copy.

![30](https://user-images.githubusercontent.com/84916459/140510955-97d2bf7a-1dd2-438c-8339-bf2542db0496.png)

FOR GATE LEVEL STIMULATION PROCESS

In this we are going to do Gatelevel simulation. for that we are going to use following files 1.netlist.v 2.sky130_fd_sc_hd.v 3.testbench.v use the following code for gatelevel simulation : iverilog netlist.v sky130_fd_sc_hd.v tb_mux.v

![32](https://user-images.githubusercontent.com/84916459/140510984-7a7da4d1-4fa5-46c5-b10c-afa2433809e0.png)
