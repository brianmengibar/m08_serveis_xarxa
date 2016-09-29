#Practica 1
##**Brian Mengibar Garcia**

**Totes com a root:**
#1-
	a) ip addr add 172.16.0.10/24 dev enp5s0
	b) ping 172.16.0.11

#2-
	arp 172.16.0.11
	Address                  HWtype  HWaddress           Flags Mask            Iface
	172.16.0.11               ether   40:8d:5c:e4:36:fa   C                     enp5s0

#3-
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
	
#4-
**Velocitat de transferencia**
	91.39 inbound
	91.45 outbound

#5-
**Camviem la MTU**
	ip link set ethernet0 mtu 9000
	
**Comprovem quina es la velocitat obtinguda**
	482.95 inbound
	482.86 outbount

#6-
**Mostrem les conexions**
	mcli con show

**Comprovem l'estatus**
	nmcli dev status
	
**Afegim la nova IP des de nmcli**
	nmcli con add con-name net-eth0 ifname eth0 type ethernet ip4 172.16.0.10/24
	Connection 'net-eth0' (98619b48-2ef2-4d4f-b9ec-cad19b330324) successfully added.

#7-
	/etc/resolv.conf
	
#8-
**Si hem fet manualment el fitxer primer tenim que fer un reload**
	nmcli con reload

**Seguidament fem un up**
	nmcli con up net-eth0 

	
