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

## Oppsett av virtuell maskin (Employee 2)





