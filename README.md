# IPtables

1)
#!/bin/sh
	#Este script reinicia los iptables
~~~
	read "quieres reiniciar los iptables? (s/n):" respuesta
	if [ $respuesta = 's' ] 
	then 
		iptables-restore < /etc/network/iptables.up.rules
	else
		echo "no has hecho nada"
	fi
	
	exit 0
~~~

2)
#!/bin/bash
~~~
	./iptables-rules
	
	#Guarda las reglas y reinicia el firewall
	/sbin/iptables-save | sudo tee /etc/sysconfig/iptables
	service iptables restart
	
	#Inicia los iptables al arrancar
	chkconfig iptables on
	
	exit 0
~~~

3)
#!/bin/sh
~~~
	#Este script reiniciara TODAS las reglas de iptables
	
	sudo iptables-restore < /root/firewall/iptables_reset
	
	exit 0
~~~	
4)
#!/bin/sh
~~~
	echo "Parando el firewall y borrando todos..."
	iptables -F
	iptables -X
	iptables -t nat -F
	iptables -t nat -X
	iptables -t mangle -F
	iptables -t mangle -X
	
	exit 0
~~~
