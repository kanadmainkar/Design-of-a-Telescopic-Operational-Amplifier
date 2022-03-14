# Design of a Telescopic Cascode Operational Amplifier
This repository presents the design of a Telescopic Cascode Operational Amplifier on 28nm CMOS process using Synopsys Custom Compiler. This design is a hackathon submission for Cloud Based Analog IC Design Hackathon conducted by VLSI System Design (VSD) & IIT Hyderabad.

## Table of Contents
1. [Abstract](#abs)
2. [Circuit Details](#cd)
3. [Reference Circuit](#rc)
4. [Final Circuit](#fc)
5. [Simulations](#sim)
6. [Results](#res)
7. [Netlist](#net)
8. [Acknowledgments](#ack)
9. [References](#ref)
10. [Author](#au)
<a name="abs"></a>
## Abstract
A telescopic opamp by its structure benefits from higher gain and lower power dissipation as compared to its two stage conventional opamp counterparts. These kind of opamps can be beneficial in applications where a large gain is required such as biomedical applications. Although a telescopic opamp structure has higher gain, it suffers from a higher number of poles and zeroes which one has to worry about, as well as it has a lower voltage swing at the output as compared to a conventional opamp due to increased number of transistors. 

<a name="cd"></a>
## Circuit Details
Telescopic structure came into existence when the conventional opamp stages weren’t enough to provide a certain amount of required gain. Hence these circuits have a cascoded input differential stage. This cascode structure allows for a higher output gain which when multiplied by the gm of the input transistor, presents a much higher gain than the simple opamp stage. For further gain, the current mirrors used to convert a differential strage to single ended stage is also cascoded to get an even higher output impedance which in turn provides a higher overall gain. The overall gain of the telescopic cascode stage will be equal to:  

<p align = 'center'>
<img src='https://user-images.githubusercontent.com/100680231/156145264-dfaf1265-db50-4353-b020-0dcf4623fd68.png'>

</p>
As one can see, this is substantially larger than the simple opamp stage. We can also see as there are more numbers of nodes in this circuit we get more number of poles due to the parasitic capacitances present at these nodes. Although the dominant pole frequency still remains at: 

<p align = 'center'>
<img src='https://user-images.githubusercontent.com/100680231/156145418-9ef40bf5-3510-449d-b5f9-81fc776d7877.png'>
  
</p>
This means that there is no significant difference in the bandwidth of the opamp. The output swing of the opamp will be: 

<p align = 'center'>
<img src='https://user-images.githubusercontent.com/100680231/156145520-10db68a4-0247-4b62-8328-8260792a6ce7.png'>
  
</p>
This is in fact less than the output voltage swing of the one stage opamp or conventional opamp.

<a name="rc"></a>
## Reference Circuit
<p align = 'center'>
<img src='https://user-images.githubusercontent.com/100680231/156170242-3f73d968-018d-4698-b09b-d5851cc36290.png'>
</p>

  - The circuit requires a current mirror to copy the current from one branch to the other so that the output can be single ended without making the output swing half of the fully differentrial counterpart. 
  - The two transistors forming the input differential pair need a sufficient common mode voltage to keep them in saturation. 
  - The two cascode transistors in both the cascode structures also require a bias voltage to keep them in saturation. 
  - The tail current source here shows that the tail current would be double the amount of current in each branch of the opamp.

<a name="fc"></a>
## Final Circuit
<p align = 'center'>
<img src='https://user-images.githubusercontent.com/100680231/156160003-0ef485bd-d6ee-49fa-b8dd-08eb67bb31fb.png'>
</p>

The required bias voltages are given using voltage sources present in the software. Although in practice these would be done using current mirrors and reference current sources.

<a name="sim"></a>
## Simulations
### Transient Analysis
![image](https://user-images.githubusercontent.com/100680231/156160117-c4707c48-490f-4a62-bc7d-4917113c44eb.png)

### Bode Plot
![image](https://user-images.githubusercontent.com/100680231/156160160-094caba7-0940-4725-a5ca-156cff8aab02.png)

<a name="res"></a>
## Results

Parameter  | Value
------------- | -------------
Overall Gain (A<sub>0</sub>)  | 40 db
Gain Bandwidth Product (GBW)  | 251 MHz
Phase Margin  | 79.9 Deg
Output Swing  | 25 mV<sub>pk-pk</sub>
Power Dissipation   | 14.7 mW

<a name="net"></a>
## Netlist
The netlist for the circuit is [here.](./FinalNetlist)

<a name="ack"></a>
## Acknowledgements
- [Kunal Ghosh](https://www.linkedin.com/in/kunal-ghosh-vlsisystemdesign-com-28084836/), Co-Founder, VLSI System Design (VSD) Corp. Pvt. Ltd.
- [IIT Hyderabad](https://iith.ac.in/)
- [Synopsys](https://www.synopsys.com/)
- [Analog IC Design Hackathon](https://www.iith.ac.in/events/2022/02/15/Cloud-Based-Analog-IC-Design-Hackathon/)

<a name="ref"></a>
## References

1. Dewangan S., Verma J. – "Design of Fully Differential Telescopic Op-amp with Common Mode Feedback in 0.25μm CMOS Technology" - Rungta International Journal of
Electrical and Electronics Engineering Volume 1 Issue 1 (March 2016)  
2. Shukla A, Girolkar A, Verma J – "REVIEW OF CASCODE & TELESCOPIC OPAMP" - Journal of Emerging Technologies and Innovative Research (May 2017) 
3. M Douglas C. da Silva, L Compassi Severo, A Gonçalves Girardi - "Design of a telescopic operational amplifier using a semi-automatic synthesis"
4. "Lecture 43 Telescopic cascode opamp" - Satish Kashyap  [[ONLINE]](https://www.youtube.com/watch?v=PfsVw7CIleM)
5. "Telescopic OPAMP Design Example" – Analog IC Design – IITM  [[ONLINE]](https://www.youtube.com/watch?v=x_jaMqvJEto&t)

<a name="au"></a>
# Author
- [Kanad Mainkar](https://www.linkedin.com/in/kanad-mainkar-854b631a4/), B.E. Instrumentation & Control, Vishwakarma Institute of Technology
