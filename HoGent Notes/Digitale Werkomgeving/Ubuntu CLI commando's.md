## Sudo

```bash
# sudo staat voor superuser do. superuser heeft meer bevoegdheden
sudo <command>

# in dit geval de lijst updaten als root-user
sudo apt update
```

Je gebruikt sudo in deze gevallen:
- Software installeren, verwijderen of aanpassen
- Systeemgebonden files aanpassen
- Services beheren (bijvoorbeeld bij SSH)
- File rechten veranderen
- Hardware of low-level system actions

Wanneer niet te gebruiken:
- Normale programma's runnen
- Malicious downloads of scripts die je niet kent/vertrouwt

**Belangrijk** - weet *waarom* je sudo moet gebruiken

---
## Apt

```bash
# geeft meer info over apt
apt --help

# geeft een volledige lijst van beschikbare software a.k.a packages
apt list

# de lijst van mogelijke packages updaten
apt update

# geeft een uitgebreidere lijst -- 'space' voor "more" - 'q' voor "quit"
apt list|more

# omgekeerde van 'more'
apt list|less

# filter de output van apt list op "ssh"
apt list|grep ssh

# filter de output van apt list op "ssh" EN "server"
apt list|grep ssh

# ignore case sensitive
-i

# invert match (toon alle results die niet de filter hebben)
-v

#geeft extra info over een bepaalde package
apt show <package-name>

#installeert deze package
apt install <package-name>
```

---

## SSH

```bash
#toont de status van een bepaalde service (kan ook iets anders zijn dan ssh)
systemctl status ssh

#start de ssh-server - hier hebben we sudo nodig omdat we dus iets doen met een service
sudo systemctl start ssh

# zorgt ervoor dat de service automatisch start bij het booten
sudo systemctl enable ssh
```

---
## Port-forwarding

Voor je port-forwarding kan gebruiken in je VM moet je dit eerst instellen via de netwerkinstellingen

|                |                                                                                                                                                                                                                      |
| -------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **Host-IP**    | Je hebt hier een aantal opties.<br>Als je wil dat enkel jouw laptop eraan kan, gebruik 127.0.0.1<br>Als je wil dat anderen via jouw laptop hieraan kunnen, dan gebruik je de private IP (of laat het leeg - default) |
| **Host Port**  | Voer hier een poort in die nog niet gebruikt wordt op het host device (check met netstat -an)<br><br>Standaard wordt er vaak 2222 gebruikt voor SSH                                                                  |
| **Guest-IP**   | Het (private) IP-adres van de VM<br>Kan je vinden met 'ip a'<br><br>Bij onze Ubuntu-server moet je het IP gebruiken dat bij "inet" staat                                                                             |
| **Guest Port** | 22 (SSH gebeurt standaard met deze poort)                                                                                                                                                                            |
Port forwarding zorgt ervoor dat het guest ip alle pakketjes kan versturen via ons host-ip.

```bash
#verbinden met de VM - doe dit in Windows CMD
#wat er staat in vierkante haakjes is soms optioneel
ssh [-p <poortnr>] <user>@<ip-adres>

#ingevuld
ssh -p 2222 lucas@127.0.0.1

#uitloggen - ssh connectie verbreken
exit
```

Er wordt dus eigenlijk via SSH een soort link gelegd a.d.h.v port forwarding, waardoor we dan bijvoorbeeld van onze eigen host-CLI kunnen verbinden met de VM-CLI