# 🖥️ Simulert IT-avdeling – Teknisk dokumentasjon

## Oversikt
Dette prosjektet simulerer en IT-avdeling i en nyetablert bedrift.  
Målet er å sette opp nettverksinfrastruktur, virtuelle maskiner for ansatte, nødvendig programvare og et ticket-system, samt dokumentere alle tekniske valg og konfigurasjoner.

## Virtuelle maskiner

## Oppsett av virtuell maskin (Employee 1)

Det ble opprettet en virtuell maskin som representerer en ansatt i bedriften.
VM-en ble satt opp ved bruk av Oracle VirtualBox og installert med Windows 10 Pro.
Operativsystemet ble levert av lærer som ISO-fil.

### VM-detaljer

| Parameter | Verdi |
|---------|------|
| VM-navn | Employee1-Win10-VM |
| Eier | Pramis |
| Virtualiseringsprogram | Oracle VirtualBox |
| Operativsystem | Windows 10 Pro |
| CPU | 1 vCPU (standard) |
| RAM | 2 GB |
| Diskstørrelse | 50 GB |
| Disk-type | VDI (dynamisk allokert) |
| Nettverksmodus | Bridged |
| Bruker | Employee 1 | 
| Passord | ikke lagret av sikkerhetshensyn |
| IP-adresse | Tildelt via DHCP |

### Oppsett og konfigurasjon
- Base Memory ble satt til 2048 MB (2 GB RAM)
- Boot-rekkefølge under installasjon var: Floppy, Optical og Hard Disk
- VM-en ble konfigurert til å fungere som en ansattmaskin i det lokale nettverket
- Nettverksmodus **Bridged** ble valgt for å gi VM-en direkte tilgang til LAN

### Eventuelle utfordringer
Det oppstod ingen kritiske problemer under oppsettet av den virtuelle maskinen.



## Nettverksoppsett

Nettverket er satt opp som et lokalt nettverk (LAN) med **stjernetopologi**.
I denne topologien er ruteren det sentrale punktet som alle enheter er koblet til.

### Nettverkstopologi
**Topologi:** Stjernetopologi  
**Sentralt punkt:** Ruter  

Alle enheter i nettverket kommuniserer via ruteren, inkludert:
- IT-avdelingens PC
- Ansattes virtuelle maskiner (VM)
- Andre tilkoblede enheter

Dette gjør nettverket oversiktlig, enkelt å administrere og lett å feilsøke.

![Stjernetopologi nettverk](Images/Stjerne%20topologi.drawio.png)


### Tilbakestilling av ruter
Ruteren ble først tilbakestilt til fabrikkinnstillinger for å sikre et rent
utgangspunkt før konfigurasjon.

### Konfigurasjon av ruter
Ruteren ble konfigurert via webgrensesnitt med følgende innstillinger:
- Trådløst nettverk (SSID) satt til et passende navn
- Nettverket ble sikret med **WPA2-Personal** og passord
- Ruteren fungerer som default gateway og DHCP-server

### IP-adressering
Alle enheter i nettverket mottar IP-adresser automatisk via DHCP.
Dette inkluderer både fysiske maskiner og virtuelle maskiner.

### Tilkobling av virtuell maskin
Virtuelle maskiner er koblet til nettverket ved bruk av **Bridged network mode**
i Oracle VirtualBox. Dette gjør at VM-ene opptrer som egne enheter i nettverket
og mottar IP-adresser direkte fra ruteren.

## IP-adressering

Det lokale nettverket benytter private IP-adresser.
Ruteren fungerer som **default gateway** og **DHCP-server**, og tildeler
IP-adresser automatisk til tilkoblede enheter.

### Ruter (LAN)
Ruterens LAN-IP-adresse ble endret fra standardinnstillingen
`192.168.0.1` til `192.168.1.45`.
Denne adressen fungerer som **default gateway** for alle enheter i nettverket.

### IP-oppsett
- IT-avdelingens PC er konfigurert med **statisk IP-adresse**
- Ansattes maskiner mottar IP-adresser automatisk via **DHCP**
- Alle enheter befinner seg i samme subnett

### Enheter i nettverket

| Enhet | Rolle | IP-adresse | Subnet mask | Default gateway |
|-----|------|-----------|-------------|----------------|
| Ruter | Gateway / DHCP | 192.168.1.45| 255.255.255.0 | - |
| IT-PC | IT-avdeling | 192.168.1.50 | 255.255.255.0 | 192.168.1.45 |
| Employee1-Win10-VM | Ansatt | Tildelt via DHCP | 255.255.255.0 | 192.168.1.45 |
| Employee2.win10 | Ansatt | Tildelt via DHCP | 255.255.255.0 | 192.168.1.45 |

DHCP benyttes for ansattemaskiner for å forenkle administrasjon,
mens statisk IP brukes på IT-avdelingens PC for stabil tilgang.


### Kommentar
Endring av ruterens LAN-IP medfører at tilkoblede enheter må fornye
sin IP-adresse for å kommunisere korrekt i nettverket

## 🖥️ IT-avdelingens PC

IT-avdelingens PC brukes som hovedmaskin for drift, fjernsupport,
dokumentasjon og håndtering av IT-saker i bedriften.

---

### 🔹 Systeminformasjon – IT-avdelingens PC

| Parameter | Verdi |
|---------|------|
| Enhetsnavn | DESKTOP-VVB7T5U |
| Rolle | IT-avdeling |
| Maskintype | Fysisk PC |
| Prosessor | Intel® Core™ i5-7200U CPU @ 2.50 GHz |
| RAM | 8 GB (7.86 GB tilgjengelig) |
| Systemtype | 64-bit operativsystem, x64-basert prosessor |
| Operativsystem | Windows 10 Pro |
| Versjon | 22H2 |
| IP-adresse | Statisk IP |
| Nettverk | Lokalnettverk (LAN) |
| Parameter | Verdi |
| Brukernavn | PrSt |
| Rolle | IT-avdeling (administrator) |
| Passord | ikke lagret av sikkerhetshensyn |
| Funksjon | Drift, fjernsupport, dokumentasjon |

---

### 🔹 Tanke av PC

IT-avdelingens PC ble tanket ved bruk av en **tom harddisk**.
Etter montering av harddisken ble **Windows 10 installert fra ISO-fil**.

Tanking ble utført for å sikre et rent og kontrollert utgangspunkt,
med korrekt operativsystem og grunnoppsett før videre konfigurasjon
og installasjon av nødvendig programvare.

---

### 🔹 Programvarevalg 

Følgende programvare ble installert på IT-avdelingens PC basert på
behov for drift, support og dokumentasjon:

- **OBS Studio**  
  Brukes til skjermopptak og dokumentasjon av IT-arbeid, inkludert
  Remote Desktop-tilkoblinger og løsning av tickets.

- **Python**  
  Brukes for å kjøre scripts og støtte ticket-systemet som benyttes
  til håndtering av IT-saker fra ansatte.

- **Remote Desktop Connection (mstsc)**  
  Brukes for å koble til ansattes maskiner og gi fjernsupport.

Programvaren ble valgt fordi den er relevant for IT-drift og ofte
benyttes i profesjonelle IT-miljøer.

---

### 🔹 Brukte tjenester

Følgende tjenester ble brukt på IT-avdelingens PC:

- **Remote Desktop Service (RDP)** – muliggjør fjernsupport
- **Windows Firewall** – beskytter systemet og tillater nødvendige tjenester
- **Ticket-system** – brukes til mottak og håndtering av IT-saker
- **HTTP-tjeneste** – brukt ved testing av lokal HTTP-server
- **DHCP-tjeneste (ruter)** – tildeler IP-adresser automatisk til enheter i nettverket

Disse tjenestene dekker grunnleggende behov for drift, sikkerhet
og support i en IT-avdeling.


---

### 🔹 Formål med IT-avdelingens PC

IT-avdelingens PC brukes til:
- Fjernsupport av ansatte
- Dokumentasjon av IT-arbeid
- Løsning og håndtering av tickets
- Drift og administrasjon av IT-tjenester


## Ticket-løsninger

Følgende tickets ble mottatt og behandlet av IT-avdelingen som en del av
simuleringen av en IT-supporttjeneste. Alle ticket-løsninger ble dokumentert
ved hjelp av skjermopptak.

### Oversikt over løste tickets

| Ticket | Beskrivelse | Tiltak |
|------|------------|-------|
| Statisk internett | Problem relatert til nettverkstilkobling og IP-konfigurasjon | Kontroll og justering av IP-innstillinger |
| Feilsøking Wi-Fi | Manglende trådløs tilkobling | Kontroll og korrigering av fysisk nettverkstilkobling mellom ruter og switch |
| Oppdater drivere | Updaterte eller manglende drivere | Oppdatering av nødvendige drivere |
| Personalisering | Tilpasning av brukerinnstillinger | Endring av bakgrunnsbilde |
| HTTP-server | Behov for lokal webserver | Oppsett og testing av enkel HTTP-server |

### Dokumentasjon
Alle tickets ble løst av IT-avdelingen og dokumentert med skjermopptak som viser
arbeidsprosess, feilsøking og endelig løsning.

## Ticket-løsninger

Alle tickets ble løst av IT-avdelingen og dokumentert med skjermopptak.
Under hver ticket er det lagt inn videodokumentasjon som viser løsning og prosess.

### 📌 Statisk internett
Problem relatert til nettverkstilkobling og IP-konfigurasjon.  
Løsning: Kontroll og justering av IP-innstillinger.

 **Video:**
- [Statisk internett](Videos/statisk_ip_adress.mp4)

---
### 📌 Feilsøking av Wi-Fi
Det trådløse nettverket var ikke tilgjengelig for brukerne. Ved feilsøking ble det avdekket at problemet ikke var relatert til programvare eller konfigurasjon, men til fysisk tilkobling. Ruteren var ikke korrekt koblet til switch med nettverkskabel. Etter at ruteren ble koblet riktig til switchen, fungerte det trådløse nettverket som forventet. Denne ticketen ble løst gjennom fysisk kabling og ble derfor ikke dokumentert med skjermopptak.

### 📌 Oppdater drivere
Problem med utdaterte eller manglende drivere.  
Løsning: Oppdatering av nødvendige systemdrivere.

**Video:**
- [Oppdater drivere](Videos/drivere.mp4)

---

### 📌 Personalisering
Behov for tilpasning av brukerinnstillinger.  
Løsning: Endring av bakgrunnbilde.

**Video:**
- [Personalisering](Videos/personalisering.mp4)

---

### 📌 HTTP-server
Behov for lokal webserver for testing og demonstrasjon.  
Løsning: Oppsett og testing av enkel innebyd python HTTP-server.

**Video:**
- [hTTP-server](Videos/HTTP-Server%20(1).mp4)









