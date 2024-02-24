## TP SEMICONDUCTING DEVICES

### 

```
go atlas
mes space.mult=1.0
#here we define the dimensions respect to y axe and x axe (12µm x 5µm)
# x from 0 to 12 microns  
x.mesh loc= 0.00 spac=0.5
x.mesh loc= 3 spac=0.2
x.mesh loc= 5.00 spac=0.25
x.mesh loc= 7.00 spac=0.25
x.mesh loc= 9.00 spac=0.2
x.mesh loc= 12.00 spac=0.5

#from 0 to 5 microns 
y.mesh loc=0.00 spac=0.01
y.mesh loc=1.00 spac=0.01
y.mesh loc=2 spac=0.2
y.mesh loc=5.00 spac=0.4

region num=1 silicon

#definition of the electrodes 
electr name=anode x.min=0 length= 12
electr name=cathode bottom

## HERE WE DEFINE THE DIFFERENT DOPOING REGION AND LEVEL (N N for our case)
# definition of the doping region N-epi doping
doping n.type conc=5.0e16
#....N+ doping
doping n.type conc=1.0e20 x.min=0 x.max=12 y.top=2 y.bot=5 uniform

# pour enregistrer la stucture qu'on a defini 
save outf=diode_v1.str

model conmob fldmob srh auger bgn print

# Pour definir les differents auxquels on veut acceder 
output con.band val.band E.field charge

# below we have defined the work function at 4.97 eV
contact name=anode workf=4.97

method newton
solve init
save outf=diodeex01_0.str

#WE use the function below to show the graphic 
tonyplot diodeex01_0.str

#Calcul of the characteristic I(V)
log outfile=diodeex01.log
solve vanode=0 vstep=0.05 vfinal=1 name=anode
tonyplot diodeex01.log
quit
```

doping concentration is differente from electron density

at the surface we have almost 0 [elecron](PN%20JUNCTION.md?fileId=244792182)

![image (3).png](.attachments.244515378/image%20%283%29.png)

distance from the top to bottom on x axes

value of parameter in y axes

the multicolor line is the doping region due to the diffusion between high and low

### Main script :

```

```

### The current versus voltage

```
#Calcul I(V)

log outfile=diodeex01.log


solve vanode=0 vstep=0.05 vfinal=1 name=anode

tonyplot diodeex01.log
```

![image.png](.attachments.244515378/image.png)By biasing the curent increase

### Let's try to see the difference between different voltage of applied on anode

with this script in plus

```

#calcul grandeur Vb à Vg=0
solve vanode=0.0
save outfile=diode00.str
tonyplot diode00.str 
#calcul grandeur n,V à 0.9
solve vanode=0.9
save outfile=diode0.9str
tonyplot diode09.str 
#calcul grandeur n,V à 0.2
solve vanode=0.2
save outfile=diode02.str
tonyplot diode02.str
#calcul grandeur n,V à 0.9
solve vanode=0.6
save outfile=diode06.str
tonyplot diode06.str 
 
```

#### For the conduction band

|  |
|--|

![image (4).png](.attachments.244515378/image%20%284%29.png)  
![image (5).png](.attachments.244515378/image%20%285%29.png)

#### we see that the conduction band is lower when we apply voltage on anode we obtain a positive slope because we will get more electron in this area

#### __For the Electric Field__

![image (6).png](.attachments.244515378/image%20%286%29.png)  
![image (7).png](.attachments.244515378/image%20%287%29.png)

### For a voltage of 0.6 V we see that the Electric Field goes down

#### For the potential

#### ![image (8).png](.attachments.244515378/image%20%288%29.png)

![image (9).png](.attachments.244515378/image%20%289%29.png)  
We see that with 0 voltage the potential is constant while with 0.6V the evolution is linear with a negative slope to reduce the barrier

### for the elctron concentration

![image (10).png](.attachments.244515378/image%20%2810%29.png)  
![image (11).png](.attachments.244515378/image%20%2811%29.png)

### We see that at 0 ( on the surface ) the electron concentration for 0 V is lower than when we apply 0.6V

## __Conclusion__ :

## these first studies allow us to get to know SILVACO and its different functions the schottky diode is really paticular as we saw on this report the barrier depend on the voltage; More voltage less barrier, electron flow easily.

```
SEMICONDUCTING DEVICES 
LABWORK : 
SIMULATION OF SCHOTTKY DIODE
BY ISSA SIDIBE  
Introduction : 

Experimentation with SILVACO 
Deckbuild code with comments 

Deck build 
It is the starting point of each exprimention with silvaco 
It is use to write the script which will define the properties of the material we want to study (dimensions, materials, doping level, etc.)
Main script 
go atlas
mes space.mult=1.0
#here we define the dimensions respect to y axe and x axe (12µm x 5µm)
# x from 0 to 12 microns  
x.mesh loc= 0.00 spac=0.5
x.mesh loc= 3 spac=0.2
x.mesh loc= 5.00 spac=0.25
x.mesh loc= 7.00 spac=0.25
x.mesh loc= 9.00 spac=0.2
x.mesh loc= 12.00 spac=0.5

#from 0 to 5 microns 
y.mesh loc=0.00 spac=0.01
y.mesh loc=1.00 spac=0.01
y.mesh loc=2 spac=0.2
y.mesh loc=5.00 spac=0.4

region num=1 silicon

#definition of the electrodes 
electr name=anode x.min=0 length= 12
electr name=cathode bottom

## HERE WE DEFINE THE DIFFERENT DOPOING REGION AND LEVEL (N N for our case)
# definition of the doping region N-epi doping
doping n.type conc=5.0e16
#....N+ doping
doping n.type conc=1.0e20 x.min=0 x.max=12 y.top=2 y.bot=5 uniform

# pour enregistrer la stucture qu'on a defini 
save outf=diode_v1.str

model conmob fldmob srh auger bgn print

# Pour definir les differents auxquels on veut acceder 
output con.band val.band E.field charge

# below we have defined the work function at 4.97 eV
contact name=anode workf=4.97

method newton
solve init
save outf=diodeex01_0.str

#WE use the function below to show the graphic 
tonyplot diodeex01_0.str

#Calcul of the characteristic I(V)
log outfile=diodeex01.log
solve vanode=0 vstep=0.05 vfinal=1 name=anode
tonyplot diodeex01.log
quit
```