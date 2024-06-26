**SIMULATION AND IMPLEMENTATION OF LOGIC GATES , ADDER AND SUBTRACTOR**

**AIM:**

To simulate and synthesis Logic Gates,Adders and Subtractor using Vivado 2023.2.

**APPARATUS REQUIRED:**

Vivado 2023.2

**PROCEDURE:**

STEP:1 Start the Vivado, Select and Name the New project.

STEP:2 Select the device family, device, package and speed.

STEP:3 Select new source in the New Project and select Verilog Module as the Source type.

STEP:4 Type the File Name and Click Next and then finish button. Type the code and save it.

STEP:5 Select the Behavioural Simulation in the Source Window and click the check syntax.

STEP:6 Click the simulation to simulate the program and give the inputs and verify the outputs as per the truth table.


**LOGIC GATES:**

**LOGIC DIAGRAM:**

![image](https://github.com/navaneethans/VLSI-LAB-EXPERIMENTS/assets/6987778/ee17970c-3ac9-4603-881b-88e2825f41a4)

**VERILOG CODE:**

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
**OUTPUT:**
![320856511-3c433290-2fc2-407d-90e4-1e1c24758fb0](https://github.com/Aravind00033/VLSI-LAB-EXP-1/assets/160571380/2a8a5d84-f8ae-4eb2-a00e-45d8dd89315d)



**HALF ADDER:**

**LOGIC DIAGRAM:**

![image](https://github.com/navaneethans/VLSI-LAB-EXPERIMENTS/assets/6987778/0e1ecb96-0c25-4556-832b-aeeedfdfe7b9)

**VERILOG CODE:**

```
module halfadder(a,b,sum,carry);
input a,b;
output sum,carry;
xor g1(sum,a,b);
and g2(carry,a,b);
endmodule
```
**OUTPUT:**
![311255308-8251c978-56b6-4c86-9d0f-de057f5664ec](https://github.com/Aravind00033/VLSI-LAB-EXP-1/assets/160571380/5aad7fb8-e85b-46a2-a50e-27004c54eb1f)


**FULL ADDER:**

**LOGIC DIAGRAM:**

![image](https://github.com/navaneethans/VLSI-LAB-EXPERIMENTS/assets/6987778/9bb3964c-438f-469d-a3de-c1cca6f323fb)

**VERILOG CODE:**
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
**OUTPUT:**

![311255367-90529bb3-c1dc-4ae2-8b1f-4b94e6afd20a](https://github.com/Aravind00033/VLSI-LAB-EXP-1/assets/160571380/09193000-5ccc-45a6-9714-b6539860f940)


**HALF SUBTRACTOR:**

**LOGIC DIAGRAM:**

![image](https://github.com/navaneethans/VLSI-LAB-EXPERIMENTS/assets/6987778/731470b7-eb4e-49f8-8bb7-2994052a7184)

**VERILOG CODE:**

```
module halfsubtractor(a,b,diff,borrow);
input a,b;
output diff,borrow;
xor g1(diff,a,b);
and g2(borrow,~a,b);
endmodule
```

**OUTPUT:**
![311255336-087e940b-db2a-4c33-a302-a3cf30a1f4b6](https://github.com/Aravind00033/VLSI-LAB-EXP-1/assets/160571380/909df8df-db38-4961-b483-c5d1a1b2139a)


**FULL SUBTARCTOR:**

**LOGIC DIAGRAM:**

![image](https://github.com/navaneethans/VLSI-LAB-EXPERIMENTS/assets/6987778/d66f874b-c1f2-44b3-a035-7149b56430c1)

**VERILOG CODE:**

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

**OUTPUT:**
![311255872-3597c920-691b-424c-937a-42720ff66df0](https://github.com/Aravind00033/VLSI-LAB-EXP-1/assets/160571380/f578a4cd-5e5d-4b1c-a210-b9d28636ef34)


**8 BIT RIPPLE CARRY ADDER:**

**LOGIC DIAGRAM:**

![image](https://github.com/navaneethans/VLSI-LAB-EXPERIMENTS/assets/6987778/7385a408-40a5-4203-8050-b72818622d79)

**VERILOG CODE:**

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

**OUTPUT:**

![311529315-e90aa804-085f-489b-8ebc-eda7686ec7b3](https://github.com/Aravind00033/VLSI-LAB-EXP-1/assets/160571380/be7571cb-0b08-49e1-9584-319c0d4ad525)



**RESULT:**

Hence Logic Gates,Adders and Subtractor are simulated and synthesised using Vivado 2023.2


