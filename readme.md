# 🖥️ Simulert IT-avdeling – Teknisk dokumentasjon

## Oversikt
Dette prosjektet simulerer en IT-avdeling i en nyetablert bedrift.  
Målet er å sette opp nettverksinfrastruktur, virtuelle maskiner for ansatte, nødvendig programvare og et ticket-system, samt dokumentere alle tekniske valg og konfigurasjoner.

---

## Nettverkstopologi

Nettverket er bygget som et **lokalt nettverk (LAN)** ved bruk av én ruter.

- Ruteren fungerer som **default gateway** og **DHCP-server**
- Alle enheter er koblet til samme lokale nettverk
- IT-avdelingens PC kan fjernstyre de ansattes maskiner ved hjelp av **Remote Desktop Protocol (RDP)**

**Topologi:** Stjernetopologi  
**Nettverkstype:** LAN

### Tilkoblede enheter
- Ruter
- IT-avdelingens PC (fysisk maskin)
- Ansatt virtuell maskin – Pramis
- Ansatt virtuell maskin – Stian

---

## IP-adressering

Nettverket benytter et privat IP-adresseområde levert av ruteren.

**IP-område:** ``  
**Subnettmaske:** `255.255.255.0`

| Enhet | Rolle | IP-adresse | Kommentar |
|-----|------|-----------|-----------|
| Ruter | Gateway | | DHCP aktivert |
| IT-PC | IT-avdeling | | Statisk IP |
| Employee1-Pramis | Ansatt |  | DHCP |
| Employee2-Stian | Ansatt | 192.168.1.245 | DHCP |

IP-adresser for de ansattes maskiner tildeles automatisk via DHCP.

---

## Brukere og roller

Brukere er delt inn i to hovedroller: **Ansatt** og **IT-avdeling**.

| Brukernavn | Maskin | Rolle | Tilganger |
|----------|--------|-------|-----------|
| itadmin | IT-PC | IT-avdeling | Administrator, RDP, ticket-system |
| Employee1 | Employe1.WIN10 | Ansatt | Standardbruker |
| Employee2 | Employee2.win10 | Ansatt | Standardbruker |

**Rollebeskrivelse:**
- **Ansatt:** Standard brukerrettigheter, daglig arbeid, mottar IT-støtte via tickets
- **IT-avdeling:** Administrativ tilgang, systemvedlikehold, fjernsupport og håndtering av tickets

---

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









## Installert programvare


### Ansattes virtuelle maskiner
- Operativsystem (Windows)
- Remote Desktop aktivert

---

## Dokumentasjon 

### Teknisk dokumentasjon inkluderer
- Nettverkstopologi
- IP-adresser
- Brukere og roller
- Installerte tjenester og programvare


---

## Forfattere
- Pramis  
- Stian

