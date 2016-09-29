#Practica 1
##**Brian Mengibar Garcia**

**Totes com a root:**
**1- Configureu dos ordinadors fent servir la comanda ip amb dues adreces del rang 172.16.0.0 i comproveu que es veuen entre si. Indiqueu les comandes que heu utilitzat a)per configurar-les b) per comprovar que es veuen.**
	a) ip addr add 172.16.0.10/24 dev enp5s0
	b) ping 172.16.0.11

**2-Com podem descobrir l'adreça mac d'un altre dispositiu de la nostra xarxa (que no sigui el nostre)? Indiqueu-ne les comandes i la sortida.**
	arp 172.16.0.11
	Address                  HWtype  HWaddress           Flags Mask            Iface
	172.16.0.11               ether   40:8d:5c:e4:36:fa   C                     enp5s0

**3-Com podem canviar el nom d'una interfície de xarxa amb la comanda ip? Poseu exemple**
**Primer descactivem la superficie**
	ip link set enp5s0 down

**Posem el nou nom**
	ip link set enp5s0 name ethernet0

**Comprovem**
	ip a s

**Activem la superficie**
	ip link set ethernet0 up

**Comprovem**
	ip a s
	
**4-Busqueu el paquet RPM per a la utilitat netperf i instal.leu-lo (copieu netperf al directori cp netperf /usr/local/bin per tal que sigui accessible desde qualsevol lloc). Arrenqueu el servidor en una de les màquines i el client en l'altra tot comprovant la velocitat que obtenim entre els dos. Indiqueu quina es la velocitat obtinguda.**
**Velocitat de transferencia**
	91.39 inbound
	91.45 outbound

**5-Canvieu ara la MTU de les interfícies de xarxa dels dos ordinadors a un valor de 9000 bytes. comproveu de nou quina és la velocitat obtinguda. Expliqueu els resultats tot comparant-los.**
**Camviem la MTU**
	ip link set ethernet0 mtu 9000
	
**Comprovem quina es la velocitat obtinguda**
	482.95 inbound
	482.86 outbount

**6-Realitzeu ara la mateixa configuració estàtica d'adreces IP amb la comanda nmcli. Indiqueu-ne els passos.**
**Mostrem les conexions**
	mcli con show

**Comprovem l'estatus**
	nmcli dev status
	
**Afegim la nova IP des de nmcli**
	nmcli con add con-name net-eth0 ifname eth0 type ethernet ip4 172.16.0.10/24
	Connection 'net-eth0' (98619b48-2ef2-4d4f-b9ec-cad19b330324) successfully added.

**7-On es troba la configuració de servidors de noms de domini?**
	/etc/resolv.conf
	
**8-Realitzeu la mateixa configuració anterior de manera permanent (ifcfg-...). Quins són els paràmetres de la comanda nmcli per tal de forçar que s'apliquin els canvis de xarxa que hem fet als fitxers?**
**Si hem fet manualment el fitxer primer tenim que fer un reload**
	nmcli con reload

**Seguidament fem un up**
	nmcli con up net-eth0 

	
