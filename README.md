# network-labs

Lab di networking e sicurezza con Cisco Packet Tracer (VLAN, routing, ACL).

## Obiettivi
- Consolidare VLAN, routing tra VLAN e ACL
- Costruire un portfolio pratico dopo CCNA e PEKIT Security ed EHE.
- Prepararmi alla certificazione Security+

## Lab
- [x] [Lab 1 – VLAN](lab01-vlan)
- [ ] Lab 2 – Routing tra VLAN
- [ ] Lab 3 – ACL per isolare IOT da CASA

# Lab 1 – Segmentazione con VLAN

## Obiettivo
Separare la rete in due VLAN su un unico switch: VLAN 10 (CASA) e VLAN 20 (IOT).

## Strumenti
- Cisco Packet Tracer 9.0.1 (macOS)
- File del lab: `lab01.pkt`

## Topologia
![Topologia](topologia.png)

## Piano delle VLAN
| VLAN | Nome | Porte switch | Dispositivi |
|------|------|--------------|-------------|
| 10 | CASA | [Fa0/1-...] | [PC...] |
| 20 | IOT | [Fa0/...] | [dispositivi...] |

## Configurazione
```
vlan 10
 name CASA
vlan 20
 name IOT
interface range [porte VLAN 10]
 switchport mode access
 switchport access vlan 10
interface range [porte VLAN 20]
 switchport mode access
 switchport access vlan 20
```

## Test eseguiti
| Test | Risultato atteso | Risultato ottenuto |
|------|------------------|--------------------|
| Ping tra due host della stessa VLAN | OK | OK |
| Ping tra host di VLAN diverse | Fallisce (nessun router) | [da verificare] |

## Problemi incontrati
nessuno 

## Cosa ho imparato
- Ho capito come una VLAN separa la rete a livello 2 anche su un unico switch fisico.
- Ho imparato ad assegnare le porte alle VLAN con la modalità access e a controllare il risultato con `show vlan brief`.
- Gli host della stessa VLAN comunicano tra loro, mentre per far parlare VLAN diverse serve un dispositivo di livello 3. Lo vedrò nel lab 2.


