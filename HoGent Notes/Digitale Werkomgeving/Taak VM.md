```bash
#3 installeer ssh en zorg dat het start bij het booten
	apt show ssh
	
	sudo apt install ssh
	
	systemctl status ssh
	
	sudo systemctl start ssh
	
	sudo systemctl enable ssh
	

#4 stel port-forwarding in via de netwerk instellingen 
	| Name   | Protocol | Host-IP   | Host port | Guest-IP  | Guest port |
	| ------ | -------- | --------- | --------- | --------- | ---------- |
	| rule 1 | TCP      | 127.0.0.1 | 2222      | 10.0.2.15 | 22         |


#5 Probeer te verbinden met de VM vanuit de cmd-line en met de public key
	scp -P 2222 id_ed25519.pub lucas@127.0.0.1:.
	
	mkdir .ssh
	
	cat id_ed25519.pub >> .ssh/authorized_keys
	
	rm id_25519.pub
	
	ssh -p 2222 lucas@127.0.0.1


#6 lijst vernieuwen met software pakketten (moeten er ongeveer 90000 zijn)
	sudo apt update
		[ apt list | wc -l ]


#7 controleer of netstat werkt en doe dan het nodige om het te installeren bv:
	netstat -n
	
	sudo apt install net-tools


#8 Gebruik het juiste commando om netstat help te raadplegen

	netstat --help
	
		#a enkel luisterende poorten tonen
		netstat -l
		
		#b enkel tcp connecties tonen
		netstat -t
		
		#c optie om IP-adressen (en poorten en users) niet te 'resolven' maar met
		#cijfers te tonen 
		netstat -n
		
		#d merk op dat sommige opties van netstat anders zijn op linux dan windows


#9 Voer het commando netstat uit en gebruik een combo van: luisterende poorten, tcp, niet resolven). Eigenlijk dus gewoon alle bovenstaand commando's combineren in één
	netstat -ltn


#10 verander de tijdszone naar die van Brussel
	timedatectl list-timezones | grep Brussels #filteren en zoeken naar juiste tz-
	#naam
	
	sudo timedatectl set-timezone Europe/Brussels #tz veranderen
	
	date #verandering controleren


#11 Installeer de Apache web server
	sudo apt install apache2 #install
	
	systemctl status apache2 #check if running
	
	netstat -tln #check op welke poorten er geluisterd wordt
				# -t betekent enkel de tcp poorten filteren
				# -l filtert op de listening poorten
				# -n geeft alles numeriek weer (dus ipv van dat er ssh staat, staat er dan 22)


#12 bezoek de default page met je normale browser. (Stel port forwarding in voor poor 80)
	| Name   | Protocol | Host-IP   | Host port | Guest-IP  | Guest port |
	| ------ | -------- | --------- | --------- | --------- | ---------- |
	| rule 2 | TCP      | 127.0.0.1 | 55000     | 10.0.2.15 | 80         |
		
		#ga nu naar 127.0.0.1:55000 -- je zal zien dat je de default page krijgt	

#13 Zorg dat je zelf eigenaar wordt van /var/www/html

		#optioneel eigenlijk
		cd /var/www/html
		
		#hiermee kunnen we zien wie er permissions heeft in de directory
		ls -l /var/www
		
		#dit is het commando om de rechten te veranderen
		sudo chown -R <username> <path>
			# chown -> change owner
			# -R -> recursive (d.w.z. ook voor alles onderliggende files en directories)
			# "sudo" want alleen de "root" mag de owner aanpassen
			
			
		#in ons geval dit dus
		sudo chown -R lucas /var/www
		
		#check met dit commando of de aanpassingen goed zijn doorgevoerd
		ls -l /var/www


#14 Maak een pagina 'vb1.html' (zorg dat je zelf eigenaar bent)
	nano /var/www/html/vb1.html
	
		# in de nano editor typ je dan gewoon iets random
		# daarna doe je ctrl+x
		# druk op 'Y' om te saven
		# en dan op enter om de suggested name te saven

#15 bezoek vb1.html met je normale web browser
	127.0.0.1:55000/vb1.html

#16 log uit op de VM zelf (exit) en log terug in via SSH, vanop de windows-cmd
#17 download het controle script en voer het uit



```