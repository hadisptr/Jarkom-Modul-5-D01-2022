# Jarkom-Modul-5-D01-2022

### Kelompok D01

<table>
    <tr>
        <th>No</th>
        <th>Nama</th>
        <th>NRP</th>
    </tr>
    <tr>
        <td>1</td>
        <td>Ananda Hadi Saputra </td>
        <td>5025201148</td>
    </tr>
    <tr>
        <td>2</td>
        <td>Nethaneel Patricio Linggar</td>
        <td>5025201180</td>
    </tr>
    <tr>
        <td>3</td>
        <td>Yehezkiel Wiradhika</td>
        <td>5025201086</td>
    </tr>
</table>

### (A) Tugas pertama kalian yaitu membuat topologi jaringan sesuai dengan rancangan yang diberikan Loid dibawah ini:

![Topologi](https://cdn.discordapp.com/attachments/856609726225973278/1049247946559987743/Topologi.png)

### (B) Untuk menjaga perdamaian dunia, Loid ingin meminta kalian untuk membuat topologi tersebut menggunakan teknik CIDR atau VLSM setelah melakukan subnetting:

![Subnet VLSM](https://cdn.discordapp.com/attachments/856609726225973278/1049249641172062239/Subnet_VLSM.png)

### Penghitungan Jumlah Subnet

| No | Subnet | Jumlah IP | Netmask |
| :---: | :---: | :---: | :---: |
| 1 | A3 | 701 | /22 |
| 2 | A7 | 256 | /23 |
| 3 | A6 | 201 | /24 |
| 4 | A2 | 63 | /25 |
| 5 | A1 | 3 | /29 |
| 6 | A8 | 3 | /29 |
| 7 | A4 | 2 | /30 |
| 8 | A5 | 2 | /30 |
| Total | 8 | 1231 | /21 |

### Tree :

![Tree](https://github.com/hadisptr/Jarkom-Modul-5-D01-2022/blob/main/Modul%205/pohon.png)

### Pembagian IP

| No | Subnet | Network ID | Subnet Mask | Wildcard | IP Broadcast | 
| :---: | :---: | :---: | :---: | :---: | :---: |
| 1 | A3 | 192.185.4.0 | 255.255.252.0  | 0.0.3.255 | 192.185.7.255 |
| 2 | A7 | 192.185.2.0 | 255.255.254.0 | 0.0.1.255 | 192.185.3.255 |
| 3 | A6 | 192.185.1.0 | 255.255.255.0 | 0.0.0.255 | 192.185.1.255 |
| 4 | A2 | 192.185.0.128 | 255.255.255.128 | 0.0.0.127 | 192.185.0.255 |
| 5 | A1 | 192.185.0.16 | 255.255.255.248 | 0.0.0.7 | 192.185.0.23 |
| 6 | A8 | 192.185.0.24 | 255.255.255.248 | 0.0.0.7 | 192.185.0.31 |
| 7 | A4 | 192.185.0.0 | 255.255.255.252 | 0.0.0.3 | 192.1985.0.3 |
| 8 | A5 | 192.185.0.4 | 255.255.255.252 | 0.0.0.3 | 192.185.0.7 |

- SETTING INTERFACE PADA GNS3

#### Strix


```
auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet static
        address 192.185.0.1
        netmask 255.255.255.252

auto eth2
iface eth2 inet static
        address 192.185.0.5
        netmask 255.255.255.252
```

#### Westalis

```
auto eth0
iface eth0 inet static
        address 192.185.0.2
        netmask 255.255.255.252
        gateway 192.185.0.1

auto eth1
iface eth1 inet static
        address 192.185.0.17
        netmask 255.255.255.248

auto eth2
iface eth2 inet static
        address 192.185.0.129
        netmask 255.255.255.128

auto eth3
iface eth3 inet static
        address 192.185.4.1
        netmask 255.255.252.0
```

### Ostania

```
auto eth0
iface eth0 inet static
        address 192.185.0.6
        netmask 255.255.255.252
        gateway 192.185.0.5

auto eth1
iface eth1 inet static
        address 192.185.1.1
        netmask 255.255.255.0

auto eth2
iface eth2 inet static
        address 192.185.0.25
        netmask 255.255.255.248

auto eth3
iface eth3 inet static
        address 192.185.2.1
        netmask 255.255.254.0
```

**Desmond**

```
auto eth0
iface eth0 inet dhcp
```

**Forger**

```
auto eth0
iface eth0 inet dhcp
```

**Blackbell**

```
auto eth0
iface eth0 inet dhcp
```

**Briar**

```
auto eth0
iface eth0 inet dhcp

```

### SSS

```
auto eth0
iface eth0 inet static
        address 192.185.0.26
        netmask 255.255.255.248
        gateway 192.185.0.25
```

### Garden

```
auto eth0
iface eth0 inet static
        address 192.185.0.27
        netmask 255.255.255.248
        gateway 192.185.0.25
```

### Eden

```
auto eth0
iface eth0 inet static
        address 192.185.0.18
        netmask 255.255.255.248
        gateway 192.185.0.17
```

### WISE

```
auto eth0
iface eth0 inet static
        address 192.185.0.19
        netmask 255.255.255.248
        gateway 192.185.0.17
```

### (C) Anya, putri pertama Loid, juga berpesan kepada anda agar melakukan Routing agar setiap perangkat pada jaringan tersebut dapat terhubung:

**Strix**

```
route add -net 192.185.0.16 netmask 255.255.255.248 gw 192.185.0.2
route add -net 192.185.0.128 netmask 255.255.255.128 gw 192.185.0.2
route add -net 192.185.4.0 netmask 255.255.252.0 gw 192.185.0.2

route add -net 192.185.1.0 netmask 255.255.255.0 gw 192.185.0.6
route add -net 192.185.0.24 netmask 255.255.255.248 gw 192.185.0.6
route add -net 192.185.2.0 netmask 255.255.254.0 gw 192.185.0.6
```

### (D) Tugas berikutnya adalah memberikan ip pada subnet Forger, Desmond, Blackbell, dan Briar secara dinamis menggunakan bantuan DHCP server. Kemudian kalian ingat bahwa kalian harus setting DHCP Relay pada router yang menghubungkannya:


#### DHCP Server

1. Pada **WISE** sebagai DHCP Server, dilakukan instalasi DHCP Server

```
echo nameserver 192.168.122.1 > /etc/resolv.conf

apt-get update
apt-get install isc-dhcp-server -y
```

2. Konfigurasi file `/etc/default/isc-dhcp-server` pada **WISE** sebagai DHCP Server

```
INTERFACES="eth0"
```

3. Konfigurasi file `/etc/dhcp/dhcpd.conf` pada **WISE** sebagai DHCP Server

```
# Forger (A2)
subnet 192.185.0.128 netmask 255.255.255.128 {
        range 192.185.0.130 192.185.0.254;
        option routers 192.185.0.129;
        option broadcast-address 192.185.0.255;
        option domain-name-servers 192.185.0.18;
        default-lease-time 600;
        max-lease-time 7200;
}

# Desmond (A3)
subnet 192.185.4.0 netmask 255.255.252.0 {
        range 192.185.4.2 192.185.7.254;
        option routers 192.190.4.1;
        option broadcast-address 192.185.7.255;
        option domain-name-servers 192.185.0.18;
        default-lease-time 600;
        max-lease-time 7200;
}

# Briar (A6)
subnet 192.185.1.0 netmask 255.255.255.0 {
        range 192.185.1.2 192.185.1.254;
        option routers 192.185.1.1;
        option broadcast-address 192.185.1.255;
        option domain-name-servers 192.185.0.18;
        default-lease-time 600;
        max-lease-time 7200;
}

# Blackbell (A7)
subnet 192.185.2.0 netmask 255.255.254.0 {
        range 192.185.2.2 192.185.3.254;
        option routers 192.185.2.1;
        option broadcast-address 192.185.3.255;
        option domain-name-servers 192.185.0.18;
        default-lease-time 600;
        max-lease-time 7200;
}

# WISE menuju Westalis (A1)
subnet 192.185.0.16 netmask 255.255.255.248 {
}
```

4. Menjalankan DHCP Server

```
service isc-dhcp-server start
```

#### DHCP Relay

Dengan topologi yang ada, **Westalis** dan **Ostania** akan bekerja sebagai DHCP Relay

1. Pada **Westalis** dan **Ostania** sebagai DHCP Relay, dilakukan instalasi DHCP Relay

```
echo nameserver 192.168.122.1 > /etc/resolv.conf

apt-get update
apt-get install isc-dhcp-relay -y
```

2. Konfigurasi file `/etc/default/isc-dhcp-relay` pada **Westalis** dan **Ostania** sebagai DHCP Relay

```
SERVERS="192.185.0.19"
INTERFACES="eth0 eth1 eth2 eth3"
OPTIONS=""
```

#### Testing

##### Forger

![DHCP Forger](https://github.com/hadisptr/Jarkom-Modul-5-D01-2022/blob/main/Modul%205/0/0.1.png)

##### Desmond

![DHCP Desmond](https://github.com/hadisptr/Jarkom-Modul-5-D01-2022/blob/main/Modul%205/0/0.2.png)

##### Briar

![DHCP Briar](https://github.com/hadisptr/Jarkom-Modul-5-D01-2022/blob/main/Modul%205/0/0.3.png)

##### Blackbell

![DHCP Blackbell](https://github.com/hadisptr/Jarkom-Modul-5-D01-2022/blob/main/Modul%205/0/0.4.png)


### (1) Agar topologi yang kalian buat dapat mengakses keluar, kalian diminta untuk mengkonfigurasi Strix menggunakan iptables, tetapi Loid tidak ingin menggunakan MASQUERADE.

Disini IP Strix sudah diubah menjadi `192.168.122.1` (static) sehingga iptables-nya disetel ke IP tersebut.

```bash
iptables -t nat -A POSTROUTING -s 192.185.0.0/21 -o eth0 -j SNAT --to-source 192.168.122.1
```


### (2) Kalian diminta untuk melakukan drop semua TCP dan UDP dari luar Topologi kalian pada server yang merupakan DHCP Server demi menjaga keamanan.

Pada Strix dilakukan konfigurasi firewall sebagai berikut

```bash
iptables -A FORWARD -p tcp -d 192.185.0.19 -i eth0 -j DROP # Drop semua TCP
iptables -A FORWARD -p udp -d 192.185.0.19 -i eth0 -j DROP # Drop semua UDP
```
iptables di atas akan melalukan drop pada semua TCP dan UDP dengan tujuan **WISE** yang memiliki IP address `192.185.0.19`

#### Testing

##### Ping google.com pada WISE setelah iptables

![Ping Firewall](https://github.com/hadisptr/Jarkom-Modul-5-D01-2022/blob/main/Modul%205/2/1.png)


### (3) Loid meminta kalian untuk membatasi DHCP dan DNS Server hanya boleh menerima maksimal 2 koneksi ICMP secara bersamaan menggunakan iptables, selebihnya didrop.

Menggunakan modul `connlimit` kita dapat melakukan reject pada koneksi yang berjumlah > 3. Script ini dijalankan pada Eden dan WISE:

```bash
iptables -A INPUT -p icmp -m connlimit --connlimit-above 2 --connlimit-mask 0 -j DROP
```
### Testing ping Eden (192.185.0.18) sebagai DNS Server dengan 3 client

![Ping Forger](https://github.com/hadisptr/Jarkom-Modul-5-D01-2022/blob/main/Modul%205/3/1.png)

![Ping Briar](https://github.com/hadisptr/Jarkom-Modul-5-D01-2022/blob/main/Modul%205/3/2.png)

![Ping Blackbell](https://github.com/hadisptr/Jarkom-Modul-5-D01-2022/blob/main/Modul%205/3/3.png)


### (4) Akses menuju Web Server hanya diperbolehkan disaat jam kerja yaitu Senin sampai Jumat pada pukul 07.00 - 16.00.

Menggunakan modul `time` kita dapat melakukan accept pada koneksi yang berjalan pada waktu yang diperbolehkan, sisanya direject. Script ini dijalankan pada Eden dan WISE:

```bash
iptables -A INPUT -m time --timestart 07:00 --timestop 16:00 --weekdays Mon,Tue,Wed,Thu,Fri -j ACCEPT
iptables -A INPUT -j REJECT
```
### Testing

Ping **Garden** (192.190.0.27) pada jam kerja

![Ping Jam Kerja](https://cdn.discordapp.com/attachments/856609726225973278/1049978185523134525/image.png)

Ping **Garden** (192.190.0.27) pada hari libur

![Ping Hari Libur](https://cdn.discordapp.com/attachments/856609726225973278/1049978394185576488/image.png)


### (5) Karena kita memiliki 2 Web Server, Loid ingin Ostania diatur sehingga setiap request dari client yang mengakses Garden dengan port 80 akan didistribusikan secara bergantian pada SSS dan Garden secara berurutan dan request dari client yang mengakses SSS dengan port 443 akan didistribusikan secara bergantian pada Garden dan SSS secara berurutan.

Pada **Ostania** dilakukan konfigurasi iptables sebagai berikut

```bash
iptables -t nat -A PREROUTING -p tcp -d 192.190.0.27 --dport 80 -m statistic --mode nth --every 2 --packet 0 -j DNAT --to-destination 192.190.0.26:80
iptables -t nat -A PREROUTING -p tcp -d 192.190.0.26 --dport 443 -m statistic --mode nth --every 2 --packet 0 -j DNAT --to-destination 192.190.0.27:443
```

Membuat zone DNS baru pada `jarkomD01.com` dan set A record ke dua IP address.

```bash
# Buat zone
echo "zone \"jarkomD01.com\" {
        type master;
        file \"/etc/bind/jarkom/jarkomD01.com\";
};" > /etc/bind/named.conf.local

# Buat foldernya
mkdir /etc/bind/jarkom/

# Buat load balancing di domain utama
echo ";
; BIND data file for local loopback interface
;
\$TTL    604800
@       IN      SOA     jarkomD01.com. root.jarkomD01.com. (
                     2021120701         ; Serial
                         604800         ; Refresh
                          86400         ; Retry
                        2419200         ; Expire
                         604800 )       ; Negative Cache TTL
;
@       IN      NS      jarkomD01.com.
@       IN      A       192.185.0.27 ; IP Garden
@       IN      A       192.185.0.26 ; IP SSS
www     IN      CNAME   jarkomD01.com.
" > /etc/bind/jarkom/jarkomD01.com

# Restart bind9
service bind9 restart
```
**Ostania**
- Masukkan perintah:
```
iptables -A PREROUTING -t nat -p tcp -d 192.185.8.1 --dport 80 -m statistic --mode nth --every 2 --packet 0 -j DNAT --to-destination 192.185.0.26:80
iptables -A PREROUTING -t nat -p tcp -d 192.185.8.1 --dport 80 -j DNAT --to-destination 192.185.0.27:80
iptables -t nat -A POSTROUTING -p tcp -d 192.185.0.26 --dport 80 -j SNAT --to-source 192.185.8.1:80
iptables -t nat -A POSTROUTING -p tcp -d 192.185.0.27 --dport 80 -j SNAT --to-source 192.185.8.1:80
```

### (6) Logging paket yang di-drop dengan standard syslog level

```
iptables -N LOGGING
iptables -A INPUT -j LOGGING
iptables -A LOGGING -m limit --limit 2/min -j LOG --log-prefix "IPTables-Dropped: " --log-level 4
iptables -A LOGGING -j DROP
```
