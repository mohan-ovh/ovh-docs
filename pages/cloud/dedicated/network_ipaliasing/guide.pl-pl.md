---
title: 'Konfiguracja adresu Additional IP jako aliasu'
excerpt: 'Dowiedz się, jak dodać kilka adresów Additional IP do interfejsu'
updated: 2023-06-15
---

> [!primary]
> Tłumaczenie zostało wygenerowane automatycznie przez system naszego partnera SYSTRAN. W niektórych przypadkach mogą wystąpić nieprecyzyjne sformułowania, na przykład w tłumaczeniu nazw przycisków lub szczegółów technicznych. W przypadku jakichkolwiek wątpliwości zalecamy zapoznanie się z angielską/francuską wersją przewodnika. Jeśli chcesz przyczynić się do ulepszenia tłumaczenia, kliknij przycisk "Zgłóś propozycję modyfikacji" na tej stronie.
>


> [!primary]
>
> Od 6 października 2022 nasze rozwiązanie "Failover IP" nazywa się teraz [Additional IP](https://www.ovhcloud.com/pl/network/additional-ip/). To nie ma wpływu na jego funkcje.
>

## Wprowadzenie

Alias IP (po angielsku IP aliasing) to specjalna konfiguracja sieci serwera dedykowanego, która umożliwia przypisanie wielu adresów IP do jednego interfejsu sieciowego.

**Z tego przewodnika dowiesz się, jak przeprowadzić taką konfigurację.**

## Wymagania początkowe

- Posiadanie [serwera dedykowanego](https://www.ovh.pl/serwery_dedykowane/){.external}, [serwera VPS](https://www.ovh.pl/vps/){.external} lub instancji [Public Cloud](https://www.ovh.pl/public-cloud/instances/){.external}.
- Dysponowanie jednym lub kilkoma adresami Additional IP.
- Zalogowanie się poprzez SSH do serwera (dostęp root).

> [!warning]
> Funkcja ta może być niedostępna lub ograniczona na [serwerach dedykowanych **Eco**](https://eco.ovhcloud.com/pl/about/).
>
> Aby uzyskać więcej informacji, zapoznaj się z naszym [porównaniem](https://eco.ovhcloud.com/pl/compare/).

## W praktyce
Poniżej przedstawiamy konfigurację dla dystrybucji bazowych.

### Debian 10/11

#### Krok 1: utworzenie pliku konfiguracyjnego

Przede wszystkim należy sporządzić kopię pliku konfiguracyjnego, aby móc go przywrócić w dowolnym momencie:

```sh
cp /etc/network/interfaces.d/50-cloud-init /etc/network/interfaces.d/50-cloud-init.bak
```

#### Krok 2: modyfikacja pliku konfiguracyjnego

Teraz można zmodyfikować plik konfiguracyjny:

```sh
editor /etc/network/interfaces.d/50-cloud-init
```

Następnie dodaj alias interfejsu:

```bash
auto eth0:0
iface eth0:0 inet static
address ADDITIONAL_IP
netmask 255.255.255.255
```

W celu upewnienia się, że alias interfejsu jest aktywowany równolegle do interfejsu `eth0`, dodaj następujący wiersz do konfiguracji eth0:

```bash
post-up /sbin/ifconfig eth0:0 ADDITIONAL_IP netmask 255.255.255.255 broadcast ADDITIONAL_IP
pre-down /sbin/ifconfig eth0:0 down
```

Jeśli masz do skonfigurowania dwa adresy Additional IP, plik /etc/network/interfaces.d/50-cloud-init musi wyglądać w taki sposób:

```bash
auto eth0
iface eth0 inet dhcp

auto eth0:0
iface eth0:0 inet static
address ADDITIONAL_IP1
netmask 255.255.255.255

auto eth0:1
iface eth0:1 inet static
address ADDITIONAL_IP2
netmask 255.255.255.255
```
Lub tak:

```bash
auto eth0
iface eth0 inet dhcp

# IP 1
post-up /sbin/ifconfig eth0:0 ADDITIONAL_IP1 netmask 255.255.255.255 broadcast ADDITIONAL_IP1
pre-down /sbin/ifconfig eth0:0 down

# IP 2
post-up /sbin/ifconfig eth0:1 ADDITIONAL_IP2 netmask 255.255.255.255 broadcast ADDITIONAL_IP2
pre-down /sbin/ifconfig eth0:1 down
```


#### Krok 3: restart interfejsu

Pozostaje tylko zrestartować interfejs:

```sh
/etc/init.d/networking restart
```

### Debian 6/7/8 i pochodne

#### Krok 1: utworzenie pliku konfiguracyjnego

Przede wszystkim należy sporządzić kopię pliku konfiguracyjnego, aby móc go przywrócić w dowolnym momencie:

```sh
cp /etc/network/interfaces /etc/network/interfaces.bak
```

#### Krok 2: modyfikacja pliku konfiguracyjnego

Teraz można zmodyfikować plik konfiguracyjny:

```sh
editor /etc/network/interfaces
```

Następnie dodaj alias interfejsu:

```bash
auto eth0:0
iface eth0:0 inet static
address ADDITIONAL_IP
netmask 255.255.255.255
```

W celu upewnienia się, że alias interfejsu jest aktywowany równolegle do interfejsu `eth0`, dodaj następujący wiersz do konfiguracji eth0:

```bash
post-up /sbin/ifconfig eth0:0 ADDITIONAL_IP netmask 255.255.255.255 broadcast ADDITIONAL_IP
pre-down /sbin/ifconfig eth0:0 down
```

Jeśli masz do skonfigurowania dwa adresy Additional IP, plik /etc/network/interfaces musi wyglądać w taki sposób:

```bash
auto eth0
iface eth0 inet static
address SERVER_IP
netmask 255.255.255.0
broadcast xxx.xxx.xxx.255
gateway xxx.xxx.xxx.254

auto eth0:0
iface eth0:0 inet static
address ADDITIONAL_IP1
netmask 255.255.255.255

auto eth0:1
iface eth0:1 inet static
address ADDITIONAL_IP2
netmask 255.255.255.255
```
Lub tak:

```bash
auto eth0
iface eth0 inet static
address SERVER_IP
netmask 255.255.255.0
broadcast xxx.xxx.xxx.255
gateway xxx.xxx.xxx.254

# IP 1
post-up /sbin/ifconfig eth0:0 ADDITIONAL_IP1 netmask 255.255.255.255 broadcast ADDITIONAL_IP1
pre-down /sbin/ifconfig eth0:0 down

# IP 2
post-up /sbin/ifconfig eth0:1 ADDITIONAL_IP2 netmask 255.255.255.255 broadcast ADDITIONAL_IP2
pre-down /sbin/ifconfig eth0:1 down
```


#### Krok 3: restart interfejsu

Pozostaje tylko zrestartować interfejs:

```sh
/etc/init.d/networking restart
```

### Debian 9+, Ubuntu 17.04+ i Arch Linux

W tych dystrybucjach przypisywanie interfejsom nazw eth0, eth1 itd. zostało zlikwidowane, dlatego od tej pory będziemy używać w sposób bardziej ogólny `systemd-network`.

#### Krok 1: utworzenie pliku konfiguracyjnego

Przede wszystkim należy sporządzić kopię pliku konfiguracyjnego, aby móc go przywrócić w dowolnym momencie:

```sh
cp /etc/systemd/network/50-default.network /etc/systemd/network/50-default.network.bak
```

#### Krok 2: modyfikacja pliku konfiguracyjnego

Teraz do pliku konfiguracyjnego można dodać adres Additional IP w następujący sposób:

```sh
nano /etc/systemd/network/50-default.network
```
```sh
[Address]
Address=22.33.44.55/32
Label=failover1 # optional
```

Label nie jest obowiązkowy, służy do sortowania poszczególnych adresów Additional IP.

#### Krok 3: restart interfejsu

Pozostaje tylko zrestartować interfejs:

```sh
systemctl restart systemd-networkd
```

### Fedora 36 i kolejne wersje

Fedora korzysta teraz z kluczowych plików (*keyfiles*).
Fedora korzystała wcześniej z profili sieci przechowywanych przez NetworkManager w formacie ifcfg w katalogu `/etc/sysconfig/network-scripts/`.<br>
NetworkManager nie tworzy już domyślnie nowych profili w tym formacie. Plik konfiguracyjny znajduje się w `/etc/NetworkManager/system-connections/`.

#### Krok 1: utworzenie pliku konfiguracyjnego

Kopia pliku źródłowego musi zostać wykonana przede wszystkim po to, aby w każdej chwili można było cofnąć:

```sh
cp -r /etc/NetworkManager/system-connections/cloud-init-eno1.nmconnection /etc/NetworkManager/system-connections/cloud-init-eno1.nmconnection.bak
```

#### Krok 2: modyfikacja pliku konfiguracyjny

> [!primary]
>
> Pamiętaj, że nazwa pliku sieciowego w naszym przykładzie może różnić się od Twojej. Dostosuj komendy do nazwy pliku. Aby uzyskać nazwę swojego interfejsu sieciowego, aby móc edytować odpowiedni plik sieciowy, możesz wykonać następujące polecenie: `ip a`.
>
> Możesz również sprawdzić podłączony interfejs za pomocą polecenia:
>
> `nmcli connection show`
>


Możesz teraz dodać Additional IP do pliku konfiguracyjnego w następujący sposób:

```sh
editor /etc/NetworkManager/system-connections/cloud-init-eno1.nmconnection
```

```sh
[ipv4]
method=auto
may-fail=false
address1=ADDITIONAL_IP/32
```

Jeśli masz dwa dodatkowe adresy Additional IP do skonfigurowania, plik konfiguracyjny powinien wyglądać następująco:


```sh
[connection]
id=cloud-init eno1
uuid=xxxxxxx-xxxx-xxxe-ba9c-6f62d69da711
type=ethernet

[user]
org.freedesktop.NetworkManager.origin=cloud-init

[ethernet]
mac-address=MA:CA:DD:RE:SS:XX

[ipv4]
method=auto
may-fail=false
address1=ADDITIONAL_IP1/32
address2=ADDITIONAL_IP2/32
```

#### Krok 3: restart interfejsu

Pozostaje tylko zrestartować interfejs:

```sh
systemctl restart NetworkManager
```

### Ubuntu 17.10 i kolejne wersje

Każdy dodatkowy adres Additional IP będzie potrzebował własnej linii w pliku konfiguracyjnym. Ma ona nazwę `50-cloud-init.yaml` i znajduje się w `/etc/netplan`.


#### Krok 1: określić interfejs

```sh
ifconfig
```

Zanotuj nazwę interfejsu i adres MAC.

#### Krok 2: utworzyć plik konfiguracyjny

Zaloguj się do serwera przez SSH i wprowadź następującą komendę:

```sh
editor /etc/netplan/50-cloud-init.yaml
```

Następnie edytuj plik, używając następującej treści: "INTERFACE_NAME", "MAC_ADDRESS" i "ADDITIONAL_IP":

```sh
network:
    version: 2
    ethernets:
        INTERFACE_NAME:
            dhcp4: true
            match:
                macaddress: MAC_ADDRESS
            set-name: INTERFACE_NAME
            addresses:
            - ADDITIONAL_IP/32
```

Zapisz i zamknij plik. Aby przetestować konfigurację, wprowadź następujące polecenie:

```sh
# netplan try
```

#### Krok 3: zastosować zmianę

Następnie wprowadź następujące polecenia, aby zastosować konfigurację:

```sh
# netplan apply
```

### CentOS, AlmaLinux (8 & 9), Rocky Linux (8 & 9), i Fedora (25 i wcześniejsze)

#### Krok 1: utworzenie pliku konfiguracyjnego

Przede wszystkim należy sporządzić kopię pliku konfiguracyjnego, aby móc wykorzystać go jako szablon:

```sh
cp /etc/sysconfig/network-scripts/ifcfg-eth0 /etc/sysconfig/network-scripts/ifcfg-eth0:0
```

#### Krok 2: modyfikacja pliku konfiguracyjny

Teraz można zmodyfikować plik eth0:0 w celu zastąpienia adresu IP:

```sh
editor /etc/sysconfig/network-scripts/ifcfg-eth0:0
```

Najpierw należy zastąpić nazwę `Device`, a następnie istniejący adres IP na otrzymany adres Additional IP:

```bash
DEVICE="eth0:0"
ONBOOT="yes"
BOOTPROTO="none" # For CentOS use "static"
IPADDR="ADDITIONAL_IP"
NETMASK="255.255.255.255"
BROADCAST="ADDITIONAL_IP"
```

#### Krok 3: restart interfejsu

Pozostaje tylko zrestartować interfejs:

```sh
ifup eth0:0
```

#### Dla AlmaLinux i Rocky Linux

Pozostaje tylko zrestartować interfejs:

```sh
systemctl restart NetworkManager
```

### Gentoo

#### Krok 1: utworzenie pliku konfiguracyjnego

Przede wszystkim należy sporządzić kopię pliku konfiguracyjnego, aby móc go przywrócić w dowolnym momencie:

```sh
cp /etc/conf.d/net /etc/conf.d/net.bak
```

#### Krok 2: modyfikacja pliku konfiguracyjnego

Teraz należy edytować plik w celu dodania do niego adresu Additional IP. W Gentoo alias dodaje się bezpośrednio w interfejsie eth0. Nie tworzymy interfejsu eth0:0, jak w przypadku Red Hat czy CentOS.

> [!warning]
>
> Domyślny adres IP serwera musi pozostać wraz z config_eth0= w tym samym wierszu. Ma to na celu zapewnienie poprawnego działania pewnych operacji właściwych dla OVH.
> 

Wystarczy więc powrócić do wiersza pod netmask **255.255.255.0** i dodać tam adres Additional IP (SERVER_IP należy zastąpić głównym adresem IP Twojego serwera).

```sh
editor /etc/conf.d/net
```

Musisz dodać to:

```bash
config_eth0=( "SERVER_IP netmask 255.255.255.0" "ADDITIONAL_IP netmask 255.255.255.255 brd ADDITIONAL_IP" )
```

Plik /etc/conf.d/net musi zawierać poniższe dane:


```bash
#This blank configuration will automatically use DHCP for any net.
# scripts in /etc/init.d. To create a more complete configuration,
# please review /etc/conf.d/net.example and save your configuration
# in /etc/conf.d/net (this file :]!).
config_eth0=( "SERVER_IP netmask 255.255.255.0"
"ADDITIONAL_IP netmask 255.255.255.255 brd ADDITIONAL_IP" )
routes_eth0=( "default gw SERVER_IP.254" )
```

Aby móc wykonać `ping` na adresie Additional IP, trzeba po prostu zrestartować interfejs sieciowy.


#### Krok 3: restart interfejsu

Pozostaje tylko zrestartować interfejs:

```sh
/etc/init.d/net.eth0 restart
```


### openSUSE

#### Krok 1: utworzenie pliku konfiguracyjnego

Przede wszystkim należy sporządzić kopię pliku konfiguracyjnego, aby móc go przywrócić w dowolnym momencie:

```sh
cp /etc/sysconfig/network/ifcfg-ens32 /etc/sysconfig/network/ifcfg-ens32.bak
```

#### Krok 2: modyfikacja pliku konfiguracyjnego

Następnie należy edytować plik /etc/sysconfig/network/ifcfg-ens32 w poniższy sposób:

```bash
IPADDR_1=ADDITIONAL_IP
NETMASK_1=255.255.255.255
LABEL_1=ens32:0
```


### cPanel (w systemie CentOS 7)

#### Kror 1: dostęp do sekcji Zarządzanie IP WHM

W Panelu klienta WHM kliknij `IP Functions`{.action} i wybierz `Add a New IP Address`{.action} z menu po lewej stronie.

![Dodaj nowy adres IP](images/Cpanel-1.png){.thumbnail}

#### Kror 2: dodaj informacje dotyczące Additional IP

Wpisz swój adres IP additional w formie "xxx.xxx.xxx.xxx" w polu "New IP or IP range to add".

Wybierz `255.255.255.255` jako maskę podsieci, po czym kliknij `Submit`{.action}.

![wprowadź nowe informacje dotyczące nowego adresu IP](images/Cpanel-2.png){.thumbnail}

> [!warning]
>
> Uwaga: Jeśli masz kilka adresów IP, które chcesz skonfigurować na tym samym bloku i jednocześnie je dodajesz, system WHM zmusi cię do użycia maski podsieci `255.255.255.0`. Nie zaleca się korzystania z tej konfiguracji, aby każdy adres IP był dodany oddzielnie, aby móc używać odpowiedniej maski podsieci `255.255.255.255`.
>

#### Kror 3: Sprawdź aktualną konfigurację IP

W sekcji `IP Functions`{.action} kliknij `Show or Delete Current IP Addresses`{.action}, aby sprawdzić, czy adres Additional IP został poprawnie dodany.

![check configured IP](images/Cpanel-3.png){.thumbnail}

### Windows Server

Serwery pod Windows często wykorzystują DHCP w konfiguracji sieci. Jeśli masz już skonfigurowany adres Additional IP lub zmieniłeś konfigurację na stały adres IP, przejdź od razu do kolejnego kroku.

Jeśli nie, musisz najpierw zmienić konfigurację sieci z DHCP na stały adres IP.

Otwórz wiersz poleceń `cmd`{.action} lub `powershell`{.action}, a następnie wpisz poniższe polecenie:

```sh
ipconfig /all
```

W rezultacie pojawi się na przykład to:

![Result of "ipconfig /all" command](images/guides-network-ipaliasing-windows-2008-1.png){.thumbnail}

Spisz następnie Twój adres IPv4, maskę podsieci, bramę domyślną oraz nazwę karty sieciowej.

Adres IP serwera w naszym przypadku to: **94.23.229.151**


Kolejne kroki możesz przeprowadzić poprzez wiersz poleceń albo poprzez interfejs graficzny:

#### W wierszu poleceń (zalecane)

W poniższych poleceniach należy zastąpić:

|Polecenie|Wartość|
|---|---|
|NETWORK_ADAPTER| Nazwa karty sieciowej (w naszym przypadku: Local Area Connection)|
|IP_ADDRESS| Adres IP serwera (w naszym przypadku: 94.23.229.151)|
|SUBNET_MASK| Maska podsieci (w naszym przypadku: 255.255.255.0)|
|GATEWAY| Brama domyślna (w naszym przypadku: 94.23.229.254)|
|ADDITIONAL_IP| Adres Additional IP, który chcesz dodać|

> [!warning]
>
> Uwaga! Jeśli wprowadzisz błędne parametry, serwer przestanie być dostępny. Wówczas trzeba będzie dokonać poprawek w trybie Winrescue lub poprzez KVM.
> 

W wierszu poleceń:

1. Zmiana ustawień na stały adres IP

```sh
netsh interface ipv4 set address name="NETWORK_ADAPTER" static IP_ADDRESS SUBNET_MASK GATEWAY
```
 
2. Zdefiniowanie serwera DNS

```sh
netsh interface ipv4 set dns name="NETWORK_ADAPTER" static 213.186.33.99
```
3. Dodanie adresu Additional IP

```sh
netsh interface ipv4 add address "NETWORK_ADAPTER" ADDITIONAL_IP 255.255.255.255
```

Od tej pory Twój adres Additional IP będzie działać.


#### Przez interfejs graficzny

1. Przejdź do menu `Uruchom`{.action} > `Panel sterowania`{.action} > `Sieć i Internet`{.action} > `Centrum sieci i udostępniania`{.action} > `Zmień ustawienia karty sieciowej`{.action} (w lewym menu).
2. Kliknij prawym przyciskiem myszy `Połączenie lokalne`{.action}.
3. Kliknij `Właściwości`{.action}.
4. Wybierz `Protokół internetowy w wersji 4 (TCP/IPv4)`{.action}, a następnie kliknij `Właściwości`{.action}.
5. Kliknij `Użyj następującego adresu IP`{.action} i wprowadź dane adresu głównego Twojego serwera, maski podsieci i bramy domyślnej uzyskane powyżej po wpisaniu polecenia `ipconfig`{.action}. (Jako preferowany serwer DNS wpisz 213.186.33.99.)

![Internet Protocol Version 4 (TCP/IPv4) Properties](images/guides-network-ipaliasing-windows-2008-2.png){.thumbnail}


> [!warning]
>
> Uwaga! Jeśli wprowadzisz błędne parametry, serwer przestanie być dostępny. Wówczas trzeba będzie dokonać poprawek w trybie Winrescue lub poprzez KVM.
> 

Następnie kliknij `Zaawansowane`{.action} (ciągle w `Ustawieniach TCP/IP`{.action}.

![Internet Protocol Version 4 (TCP/IPv4) Properties](images/guides-network-ipaliasing-windows-2008-2.png){.thumbnail}

W sekcji `Adres IP`{.action} kliknij `Dodaj`{.action} :

![Advanced TCP/IPv4 Settings](images/guides-network-ipaliasing-windows-2008-3.png){.thumbnail}

Następnie wprowadź adres Additional IP oraz maskę podsieci **255.255.255.255**.

![Advanced TCP/IPv4 Settings](images/guides-network-ipaliasing-windows-2008-4.png){.thumbnail}

Kliknij `Dodaj`{.action}.

Od tej pory Twój adres Additional IP będzie działać.

### Plesk

#### Etap 1: dostęp do interfejsu zarządzania adresami IP Plesk

W panelu konfiguracyjnym Plesk wybierz `Tools & Settings`{.action} na pasku bocznym po lewej stronie.

![dostęp do zarządzania adresami IP](images/pleskip1.png){.thumbnail}

Kliknij `IP Addresses`{.action} w **Tools & Settings**.

#### Etap 2: dodaj dodatkowe informacje IP

W tej sekcji kliknij przycisk `Add IP Address`{.action}.

![dodaj informacje IP](images/pleskip2-2.png){.thumbnail}

Wprowadź adres Additional IP w formie `xxx.xxx.xxx.xxx/32` w polu "IP address and subnet mask", a następnie kliknij `OK`{.action}.

![dodaj informacje IP](images/pleskip3-3.png){.thumbnail}

#### Etap 3: sprawdź aktualną konfigurację IP

W sekcji "IP Addresses" sprawdź, czy adres Additional IP został poprawnie dodany.

![aktualna konfiguracja IP](images/pleskip4-4.png){.thumbnail}


### FreeBSD

#### Krok 1: określenie interfejsu

Ustal nazwę głównego interfejsu sieci. W tym celu możesz użyć polecenia `ifconfig`{.action}:

```sh
ifconfig
```

W rezultacie pojawi się:

```sh
ifconfig
>>> nfe0: flags=8843 metric 0 mtu 1500
>>> options=10b
>>> ether 00:24:8c:d7:ba:11
>>> inet 94.23.196.18 netmask 0xffffff00 broadcast 94.23.196.255
>>> inet 87.98.129.74 netmask 0xffffffff broadcast 87.98.129.74
>>> media: Ethernet autoselect (100baseTX )
>>> status: active
>>> lo0: flags=8049 metric 0 mtu 16384
>>> options=3
>>> inet6 fe80::1%lo0 prefixlen 64 scopeid 0x2
>>> inet6 ::1 prefixlen 128
>>> inet 127.0.0.1 netmask 0xff000000 v comsdvt#
```

W naszym przypadku nazwą interfejsu jest **nfe0**.


#### Krok 2: utworzenie pliku konfiguracyjnego

Przede wszystkim należy sporządzić kopię pliku konfiguracyjnego, aby móc go przywrócić w dowolnym momencie:

```sh
cp /etc/rc.conf /etc/rc.conf.bak
```

#### Krok 3: modyfikacja pliku konfiguracyjnego

Edytuj plik /etc/rc.conf:

```sh
editor /etc/rc.conf
```

Następnie dopisz ten wiersz na końcu pliku ifconfig_INTERFACE_alias0=`inet ADDITIONAL_IP netmask 255.255.255.255 broadcast ADDITIONAL_IP`.

Zastąp **INTERFACE** i **ADDITIONAL_IP** odpowiednio nazwą interfejsu (określoną w pierwszym kroku) oraz Twoim adresem Additional IP. Oto przykład:


```bash
ifconfig_nfe0_alias0="inet 87.98.129.74 netmask 255.255.255.255 broadcast 87.98.129.74"
```

#### Krok 4: restart interfejsu

Pozostaje tylko zrestartować interfejs:

```sh
/etc/rc.d/netif restart && /etc/rc.d/routing restart
```

### Solaris

#### Krok 1: określenie interfejsu

Ustal nazwę głównego interfejsu sieci. W tym celu możesz użyć polecenia `ifconfig`{.action}:

```sh
ifconfig -a
```

W rezultacie pojawi się:

```sh
ifconfig -a
>>> lo0: flags=2001000849 mtu 8232 index 1 inet 127.0.0.1 netmask ff000000 e1000g0: flags=1000843 mtu 1500 index 2 inet 94.23.41.167 netmask ffffff00 broadcast 94.23.41.255 ether 0:1c:c0:f2:be:42
```

W naszym przypadku nazwą interfejsu jest więc **e1000g0**.


#### Krok 2: utworzenie pliku konfiguracyjnego

Przede wszystkim należy sporządzić kopię pliku konfiguracyjnego, aby móc go przywrócić w dowolnym momencie:

```sh
editor /etc/hostname.e1000g0:1
```

#### Krok 3: modyfikacja pliku konfiguracyjnego

W tym pliku wpisz: **ADDITIONAL_IP/32 up**, gdzie **ADDITIONAL_IP** odpowiada Twojemu adresowi Additional IP. Na przykład:

```bash
188.165.171.40/32 up
```

#### Krok 4: restart interfejsu

Pozostaje tylko zrestartować interfejs:

```sh
svcadm restart svc:/network/physical:default
```

#### Rozwiązywanie problemów

Jeśli nie udaje Ci się nawiązać połączenia między siecią publiczną a Twoim aliasem IP i podejrzewasz problem z siecią, zrestartuj serwer w [trybie Rescue](/pages/cloud/dedicated/rescue_mode) i skonfiguruj alias bezpośrednio na serwerze.

W tym celu, po zrestartowaniu serwera w trybie Rescue, uruchom następujące polecenie:

```bash
ifconfig eth0:0 ADDITIONAL_IP netmask 255.255.255.255 broadcast ADDITIONAL_IP up
```

Gdzie zastąpisz "ADDITIONAL_IP" prawdziwym Additional IP.

Następnie wystarczy wykonać ping z Twojego dodatkowego adresu IP na zewnątrz. Jeśli to działa, prawdopodobnie oznacza to, że istnieje błąd konfiguracji, który należy skorygować. Jeśli zamiast tego IP nadal nie działa, otwórz zgłoszenie do zespołu pomocy w [Panelu klienta OVHcloud](https://www.ovh.com/auth/?action=gotomanager&from=https://www.ovh.pl/&ovhSubsidiary=pl){.external} w celu przeprowadzenia dodatkowego badania.

## Sprawdź również

[Tryb bridge IP](/pages/cloud/dedicated/network_bridging)

Przyłącz się do społeczności naszych użytkowników na stronie <https://community.ovh.com/en/>.