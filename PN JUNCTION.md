```



‡Calcul I (V)

1og outfile pnjunction01_22.10g solve

vanode=0 vstep=0.05 vfinal=1 name=anode

tonyplot pnjunction01_22.10g #‡calcul grandeur Vb à Vg=0.5V solve vanode=0.5

save outfile-pnjunction05.str

tonyplot pnjunction05. str #‡calcul grandeur n, V etc à -0.2V solve vanode=-0.2

save outfile pnjunctionM02.str

tonyplot pnjunctionM02.str

```

![image.png](.attachments.244792182/image.png)

```
go atlas

mes space.mult=1.0

#

x.mesh loc= 0.00 spac=0.5

x.mesh loc= 3 spac=0.2

x.mesh loc= 5.00 spac=0.25

x.mesh loc= 7.00 spac=0.25

x.mesh loc= 9.00 spac=0.2

x.mesh loc= 12.00 spac=0.5

#

y.mesh loc=0.00 spac=0.1

y.mesh loc=1.00 spac=0.1

y.mesh loc=1.5 spac=0.05

y.mesh loc=2.00 spac=0.02
y.mesh loc=2.50 spac=0.05

y.mesh loc=5.00 spac=0.4




region num=1 silicon

electr name=anode top

electr name=cathode bot

#....P-epi doping

doping p.type conc=5e16 x.min=0 x.max=12 y.top=0 y.bot=2 uniform


#....N doping

doping n.type conc=1e18 x.min=0 x.max=12 y.top=2 y.bot=5 uniform

save outf=modif_0.str


model conmob fldmob srh auger bgn 
output con.band val.band E.field charge 
method newton

solve init

save outf=test_pn22.str

tonyplot test_pn22.str
#calcul I(V)
log outfile =diodepn.log

solve vanode=0.05 vstep=0.05 vfinal=1 name=anode

tonyplot diodepn.log

##calcul grandeur Vb a Vg=0.5V

solve vanode=0.5

save outfile=pnjunction05.str

tonyplot pnjunction05.str

##calcul grandeur n, V etc a -0.2

solve vanode=-0.2

save outfile=pnjunctionM02.str

tonyplot pnjunctionM02.str

#calc 0.8
solve vanode=-0.8

save outfile=pnjunctionM08.str

tonyplot pnjunctionM08.str

quit

```

![image (2).png](.attachments.244792182/image%20%282%29.png)