# VLSI-LAB-EXPERIMENTS
## AIM:
To simulate and synthesis Logic Gates,Adders and Subtractor using Xilinx ISE.

## APPARATUS REQUIRED:
Xilinx 14.7 Spartan6 FPGA

## PROCEDURE: 
STEP:1 Start the Xilinx navigator, Select and Name the New project. STEP:2 Select the device family, device, package and speed. STEP:3 Select new source in the New Project and select Verilog Module as the Source type. STEP:4 Type the File Name and Click Next and then finish button. Type the code and save it. STEP:5 Select the Behavioral Simulation in the Source Window and click the check syntax. STEP:6 Click the simulation to simulate the program and give the inputs and verify the outputs as per the truth table. STEP:7 Select the Implementation in the Sources Window and select the required file in the Processes Window. STEP:8 Select Check Syntax from the Synthesize XST Process. Double Click in the Floorplan Area/IO/Logic-Post Synthesis process in the User Constraints process group. UCF(User constraint File) is obtained. STEP:9 In the Design Object List Window, enter the pin location for each pin in the Loc column Select save from the File menu. STEP:10 Double click on the Implement Design and double click on the Generate Programming File to create a bitstream of the design.(.v) file is converted into .bit file here. STEP:12 Load the Bit file into the SPARTAN 6 FPGA STEP:11 On the board, by giving required input, the LEDs starts to glow light, indicating the output.

## Logic Diagram :

### Logic Gates:
![image](https://github.com/navaneethans/VLSI-LAB-EXPERIMENTS/assets/6987778/ee17970c-3ac9-4603-881b-88e2825f41a4)


### Half Adder:

![image](https://github.com/navaneethans/VLSI-LAB-EXPERIMENTS/assets/6987778/0e1ecb96-0c25-4556-832b-aeeedfdfe7b9)


### Full adder:

![image](https://github.com/navaneethans/VLSI-LAB-EXPERIMENTS/assets/6987778/9bb3964c-438f-469d-a3de-c1cca6f323fb)


### Half Subtractor:

![image](https://github.com/navaneethans/VLSI-LAB-EXPERIMENTS/assets/6987778/731470b7-eb4e-49f8-8bb7-2994052a7184)



### Full Subtractor:

![image](https://github.com/navaneethans/VLSI-LAB-EXPERIMENTS/assets/6987778/d66f874b-c1f2-44b3-a035-7149b56430c1)



### 8 Bit Ripple Carry Adder

![image](https://github.com/navaneethans/VLSI-LAB-EXPERIMENTS/assets/6987778/7385a408-40a5-4203-8050-b72818622d79)



## VERILOG CODE:
### Logic Gates:
```
module logicgate (a,b,andgate,orgate,xorgate,nandgate,norgate,xnorgate,notgate);
input a,b;  
output andgate,orgate,xorgate,nandgate,norgate,xnorgate,notgate;
and(andgate,a,b);
or(orgate,a,b);
xor(xorgate,a,b);
nand(nandgate,a,b); 
nor(norgate,a,b);
xnor(xnorgate,a,b);
not(notgate,a);
endmodule
```
### Half Adder
```
module halfadder(a,b,sum,carry);
input a,b;
output sum,carry;
xor g1(sum,a,b);
and g2(carry,a,b);
endmodule
```
### Half Subtractor
```
module halfsubtractor(a,b,diff,borrow);
input a,b;
output diff,borrow;
xor g1(diff,a,b);
and g2(borrow,~a,b);
endmodule
```
### Full Adder
```
module fadd(a,b,c,sum,carry);
input a,b,c;
output sum,carry;
wire w1,w2,w3;
xor g1(w1,a,b);
and g2(w2,a,b);
xor g3(sum,w1,c);
and g4(w3,w1,c);
or g5(carry,w3,w2);
endmodule
```
### Full Subtractor
```
module fs(a,b,bin,d,bout);
input a,b,bin; 
output d,bout;
wire w1,w2,w3;
xor g1(w1,b,bin; 
xor g2(d,w1,a);
and g3(w2,a,~w1);
and g4(w3,~b,bin);
or g5(bout,w2,w3);
endmodule
```
### 8 bit ripple carry adder
```
module ripplemod(a, b, cin, sum, cout);
input [07:0] a;
input [07:0] b;
input cin;
output [7:0]sum;
output cout;
wire[6:0] c;
fulladd a1(a[0],b[0],cin,sum[0],c[0]);
fulladd a2(a[1],b[1],c[0],sum[1],c[1]);
fulladd a3(a[2],b[2],c[1],sum[2],c[2]);
fulladd a4(a[3],b[3],c[2],sum[3],c[3]);
fulladd a5(a[4],b[4],c[3],sum[4],c[4]);
fulladd a6(a[5],b[5],c[4],sum[5],c[5]);
fulladd a7(a[6],b[6],c[5],sum[6],c[6]);
fulladd a8(a[7],b[7],c[6],sum[7],cout);
endmodule
module fulladd(a, b, cin, sum, cout);
input a;
input b;
input cin;
output sum;
output cout;
assign sum=(a^b^cin);
assign cout=((a&b)|(b&cin)|(a&cin));
endmodule
```
## OUTPUT:

### Logic Gates:
#### AND GATE
![311255430-2208a23a-e3cd-4fac-b380-ba2dbf6e6141](https://github.com/Aravind00033/VLSI-LAB-EXP-1/assets/160571380/990a82d1-5fe2-449d-8415-4675e6b515d4)

#### OR GATE
![311255471-e408ed50-1cc1-40cd-9ba9-e96de495114b](https://github.com/Aravind00033/VLSI-LAB-EXP-1/assets/160571380/e8b8ab29-36c3-43fe-b00c-a19caacbb4b4)

#### NAND GATE
![311255525-2213a916-5ef0-4647-aa01-65264823e97f](https://github.com/Aravind00033/VLSI-LAB-EXP-1/assets/160571380/251dbc92-d6b9-4aee-91ff-a3e5e07ab4e5)

#### NOR GATE
![311255822-3bedc92a-c206-49ab-9d98-672b0e89a399](https://github.com/Aravind00033/VLSI-LAB-EXP-1/assets/160571380/67c23f27-d412-4eb1-a802-83e38e54b22a)

#### XOR GATE
![311255567-c043b5b6-dbfb-44cd-8138-85173f1f8544](https://github.com/Aravind00033/VLSI-LAB-EXP-1/assets/160571380/55947596-9c65-44e1-8bd4-dc7d7b20f865)

#### XNOR GATE
![311255593-cc4bb633-d330-42ea-8247-97bfb4b383b0](https://github.com/Aravind00033/VLSI-LAB-EXP-1/assets/160571380/502978ec-3635-4758-9f1a-7217bae06a32)

#### NOT GATE
![311255638-3c7c8fb5-3ab2-43d4-9ac6-121548299a8b](https://github.com/Aravind00033/VLSI-LAB-EXP-1/assets/160571380/278aabfe-50f2-4e43-89ec-46360067b41f)

### Half Adder
![311255308-8251c978-56b6-4c86-9d0f-de057f5664ec](https://github.com/Aravind00033/VLSI-LAB-EXP-1/assets/160571380/a7634cc9-d8e4-4b95-9b43-e9dd1d3d1550)

### Half Subtractor
![311255336-087e940b-db2a-4c33-a302-a3cf30a1f4b6](https://github.com/Aravind00033/VLSI-LAB-EXP-1/assets/160571380/95699c6f-c354-4edf-b704-6270ebe219d9)

### Full Adder
![311255367-90529bb3-c1dc-4ae2-8b1f-4b94e6afd20a](https://github.com/Aravind00033/VLSI-LAB-EXP-1/assets/160571380/86a5b82c-7c5b-4811-a23a-ac7facee5ac3)

### Full Subtractor
![311255872-3597c920-691b-424c-937a-42720ff66df0](https://github.com/Aravind00033/VLSI-LAB-EXP-1/assets/160571380/25bca4d6-21b6-47ec-a77e-b7cfaf37e0dd)

### 8 Bit Ripple Carry Adder 
![311529315-e90aa804-085f-489b-8ebc-eda7686ec7b3](https://github.com/Aravind00033/VLSI-LAB-EXP-1/assets/160571380/b0f936b8-39d5-4856-955f-cf2b8857b2cd)


## RESULT:
Hence Logic Gates,Adders and Subtractor are simulated and synthesised using Xilinx ISE.


