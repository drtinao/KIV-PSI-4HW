# KIV-PSI-4HW
Fourth HW assigned in KIV/PSI
1) Popis prvků + konfigurace

Podkapitoly obsahují popis jednotlivých prvků, jež jsou přítomny ve schématu sítě. Kde je to potřeba, je popsán i postup, jaký konfigurační postup byl u daného zařízení proveden

1.a) NAT1

Reprezentuje poskytovatele internetu. Dodá IP adresu, kterou jsme identifikovatelní v rámci internetu.

1.b) R1

Router typu Cisco 7200 běžící na systému Cisco IOS - verze 15.0(1)M.

Postup konfigurace:
- "configure terminal"
  - příkaz otevře konfigurační rozhraní routeru
- "interface gigabitEthernet 0/0"
  - chci konfigurovat port, který je propojen s NAT1
- "ip address dhcp"
  - chci získat adresu pomocí dhcp
- "ip nat outside"
  - nastavení typu překladu IP adres
- "no shutdown"
  - povolení portu / rozhraní
- "exit"
  - odejdu z konfigurace konkrétního rozhraní  
- "interface gigabitEthernet 1/0"
  - chci konfigurovat port, který je propojen s R2
- "ip address 192.168.123.253 255.255.255.252"
  - nastavení síťové adresy a masky
  - dvě použitelné adresy: 192.168.123.253 a 192.168.123.254
- "ip nat inside"
  - nastavení typu překladu IP adres
- "no shutdown"
  - povolení portu / rozhraní
- "exit"
  - odejdu z konfigurace konkrétního rozhraní 
- "ip route 192.168.123.0 255.255.255.0 gigabitEthernet 1/0"
  - nastavení routovací tabulky, přidání dalšího hopu
- "access-list 1 permit 192.168.123.0 0.0.0.255"
  - vytvoření pravidla ACL, povolení všech IP z daného rozmezí
- "ip nat inside source list 1 interface gigabitEthernet 0/0 overload"
  - aplikování vytvořeného ACL pravidla na rozhraní 
- "exit"
  - odejdu z konfiguračního terminálu
- "copy running-config startup-config"
  - označím právě nastavenou kofiguraci jako startovní, zkopíruju ji
  - je potřeba potvrdit přepsání předchozí konfigurace (2x Enter)
1.c) R2

Router typu Cisco 7200 běžící na systému Cisco IOS - verze 15.0(1)M.

Postup konfigurace:


1.d) Switch1
1.e) psi-base-node-1
1.f) psi-base-node-2
