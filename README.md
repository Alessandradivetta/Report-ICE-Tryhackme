# Report: ICE room Tryhackme

Con questa repository, si vuole reportare il processo di scan di un IP target e l'exploiting di un payload malevolo sul server vulnerabile Icecast. 

**1. CONNESSIONE ALLA VPN**

**_Scaricamento del file di configurazione VPN_**

Il file di configurazione OpenVPN (.ovpn) è stato scaricato dalla sezione Accesso VPN della piattaforma TryHackMe dopo aver effettuato l’accesso con le credenziali personali.

**_Installazione di OpenVPN:_**

È stato verificato che OpenVPN fosse installato sul sistema eseguendo il comando:
```
openvpn --version
```

La connessione è stata avviata utilizzando il file di configurazione scaricato, con il seguente comando:
```
sudo openvpn --config <percorso_del_file>.ovpn
```

Per confermare il corretto instradamento del traffico attraverso la VPN, è stato controllato l’indirizzo IP.


**2. SCAN DELLA VITTIMA**

Una volta effettuato il collegamento alla VPN, dato un IP target denominato vittima, si effettua uno scan nmap con il comando:

```
nmap -v -T5 -Pn vittima
```
dove
``` -v ``` indica maggiore verbosità, ```-T5``` indica un ivello di aggressività molto alto per la scansione, ottimizzando la velocità a scapito della precisione e del rischio di rilevamento da parte di sistemi di sicurezza, e ```-Pn``` disabilita il ping.

I risultati sono i seguenti:
![6577B4B3-A5DA-4F41-951E-5801E60E53D9_1_201_a](https://github.com/user-attachments/assets/8e952963-ea9f-4ef9-9c9d-742fa5548e44)

**Servizio Microsoft Remote Desktop (MSRDP)**

Dopo aver completato la scansione, si osservano diverse porte aperte sulla macchina. Il firewall risulta disattivato, con il servizio completamente spento, lasciando così la macchina esposta. 

La porta dedicata a Microsoft Remote Desktop (MSRDP)è la numero 3389.


**Servizio sulla porta 8000**

Nmap ha rilevato un servizio HTTP in esecuzione sulla porta 8000.



**Host**

Il nome host della macchina è ICE.


