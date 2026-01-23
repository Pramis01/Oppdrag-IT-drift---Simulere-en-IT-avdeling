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
| Passord | IMkuben1337! |
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

## IT-avdelingens PC

### Tanke av PC
IT-avdelingens PC ble tanket i henhold til gitte instrukser for å sikre
korrekt operativsystem og oppsett.

### Installert programvare
- **OBS Studio**  
  Brukes til skjermopptak og dokumentasjon av arbeid, inkludert Remote Desktop.
- **Python**  
  Brukes for å kjøre scripts og støtte ticket-systemet.

---

## Remote Desktop (RDP)

Remote Desktop ble satt opp og testet mellom IT-avdelingens PC og
den ansattes virtuelle maskin.

For å kunne bruke Remote Desktop må begge maskinene være koblet til
**samme lokale nettverk (LAN)**. Når dette kravet er oppfylt, kan IT-avdelingen
koble seg direkte til den ansattes maskin ved bruk av IP-adresse.

Tilkoblingen ble utført ved bruk av **Remote Desktop Connection (mstsc)**,
og testen var vellykket. IT-avdelingen fikk full tilgang til
den ansattes skrivebord.

Skjermbilder av Remote Desktop-tilkoblingen er lagret som dokumentasjon.

---

## Programvare – IT-avdelingen

IT-avdelingen benytter følgende verktøy:
- OBS Studio for dokumentasjon
- Python for scripts og ticket-system
- Remote Desktop for fjernsupport

---

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









