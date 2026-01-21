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
| Ruter | Gateway / DHCP | 192.168.1.7| 255.255.255.0 | 192.168.1.45 |
| IT-PC | IT-avdeling | 192.168.1.50 | 255.255.255.0 | 192.168.1.45 |
| Employee1-Win10-VM | Ansatt | Tildelt via DHCP | 255.255.255.0 | 192.168.1.45 |
| Employee2.win10 | Ansatt | Tildelt via DHCP | 255.255.255.0 | 192.168.1.45 |

### Kommentar
Endring av ruterens LAN-IP medfører at tilkoblede enheter må fornye
sin IP-adresse for å kommunisere korrekt i nettverket







