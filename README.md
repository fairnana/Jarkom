
[![Review Assignment Due Date](https://classroom.github.com/assets/deadline-readme-button-22041afd0340ce965d47ae6ef1cefeee28c7c493a6346c4f15d667ab976d596c.svg)](https://classroom.github.com/a/99wpTe72)
| Name           | NRP        | Kelas     |
| ---            | ---        | ----------|
| Fairna Mustika Hermafidhanti | 5025221160 | Jaringan Komputer (A) |
| Ignatius Ida Bagus Abimanyu | 502522189 | Jaringan Komputer (A) |

## Find your topology here!

- Link: https://drive.google.com/drive/folders/1ECQD6-cQkg0DzyflG-jSxJZaGaxg0KSU?usp=sharing

- Topology distribution for groups: https://docs.google.com/spreadsheets/d/1QKEZjixTStNbdXznOalJoJS0UQ6ed23o51pP8t8eAIM/edit?gid=1757558734#gid=1757558734

## Put your topology config image here!

`Put image in here`

<br>

## Soal 1

> Topologi terdiri dari node Wortel yang berupa DNS Master*. Selain itu, terdapat pula node Pokcoy sebagai DNS Slave*, yang bertugas sebagai cadangan dari node Wortel.
> <br> </br>
> Selanjutnya terdapat node Tomat dan Taoge yang bekerja sebagai Client*, tiga buah Web Server* yaitu Bayam, Buncis, dan Brokoli, serta Mayur sebagai Router*. Buatlah topologi sesuai dengan pembagian topologi [di sini](https://docs.google.com/spreadsheets/d/1QKEZjixTStNbdXznOalJoJS0UQ6ed23o51pP8t8eAIM/edit?usp=sharing) dan konfigurasi topologi [di sini](https://drive.google.com/drive/folders/1ECQD6-cQkg0DzyflG-jSxJZaGaxg0KSU?usp=sharing). Pastikan bahwa setiap node dapat terhubung ke Internet.

> _The topology consists of a Wortel node which is a DNS Master*. In addition, there is also a Pokcoy node as a DNS Slave*, which serves as a backup for the Wortel node._
> <br> </br>
> _Furthermore, there are Tomat and Taoge nodes that work as Client*, three Web Servers*, namely Bayam, Buncis, and Brokoli, then finally Mayur as Router*. Make a topology according to the topology division [here](https://docs.google.com/spreadsheets/d/1QKEZjixTStNbdXznOalJoJS0UQ6ed23o51pP8t8eAIM/edit?usp=sharing) and the topology configuration [here](https://drive.google.com/drive/folders/1ECQD6-cQkg0DzyflG-jSxJZaGaxg0KSU?usp=sharing). Make sure that each node can connect to the Internet._

**Answer:**

- Screenshot

	![image](https://github.com/user-attachments/assets/7bbc7859-7104-438d-ab7f-5455d1a3c3c3)




- Explanation
  * Melakukan konfigurasi setiap node
  
	  **MayourRouter**  
		
		auto eth0
		iface eth0 inet dhcp
		
		auto eth1
		iface eth1 inet static
			address 10.8.1.1
			netmask 255.255.255.0
		
		auto eth2
		iface eth2 inet static
			address 10.8.2.1
			netmask 255.255.255.0
		auto eth3
		iface eth3 inet static
			address 10.8.3.1
			netmask 255.255.255.0
	 	
	  **Tomat Client**
		
		auto eth0
		iface eth0 inet static
			address 10.8.1.2
			netmask 255.255.255.0
			gateway 10.8.1.1
		
	  **Tomat Client**
		
		auto eth0
		iface eth0 inet static
			address 10.8.1.3
			netmask 255.255.255.0
			gateway 10.8.1.1
	
		
	  **Bayam Webserver**
	
		auto eth0
		iface eth0 inet static
			address 10.8.2.2
			netmask 255.255.255.0
			gateway 10.8.2.1
	
		
	   **Buncis Webserver**
		
		auto eth0
		iface eth0 inet static
			address 10.8.2.3
			netmask 255.255.255.0
			gateway 10.8.2.1
	
		
	   **Brokoli webserver**
		
		auto eth0
		iface eth0 inet static
			address 10.8.2.4
			netmask 255.255.255.0
			gateway 10.8.2.1
	
	
	   **Pokcoy DNSSlvae**
	
		auto eth0
		iface eth0 inet static
			address 10.8.2.5
			netmask 255.255.255.0
			gateway 10.8.2.1
	

	    **WortelDNS**
	
		auto eth0
		iface eth0 inet static
			address 10.8.3.2
			netmask 255.255.255.0
			gateway 10.8.3.1

	
 * Agar semua node dapat mengakses internet maka ditambahkan :
   1.	Pada konfigurasi MayurRouter : `up iptables -t nat -A POSTROUTING -o eth0 -j MASQUERADE -s 10.8.0.0/16`
   2.	Pada `/root/.bashrc` pada semua ndoe : `echo nameserver 192.168.122.1 > /etc/resolv.conf`
      
 * Melakukan testing dengan cara `ping google.com`
    
    		
 
 
 
 
<br>

## Soal 2

> Tambahkan konfigurasi untuk domain bayam.yyy.com yang mengarah ke IP node Bayam di DNS Master. Dengan cara yang sama, buat konfigurasi domain brokoli.yyy.com yang mengarah ke IP node Brokoli dan domain buncis.yyy.com yang mengarah ke IP node Buncis. Simpan semua konfigurasi dalam folder Jarkom. Selama pengerjaan soal, ubah yyy menjadi kode kelompok masing-masing (contoh: A02).
> <br> </br>
> Jangan lupa update konfigurasi kedua client agar dapat berkomunikasi dengan semua domain tersebut.


> _Add a configuration for bayam.yyy.com domain that points to the Bayam node IP in the DNS Master. In the same way, create a brokoli.yyy.com domain configuration that points to the Brokoli node IP and a buncis.yyy.com domain that points to the Buncis node IP. Save all configurations in a folder called Jarkom. For this practicum, substitute yyy with the code of each group (ex: A02).
> <br> </br> 
> Don't forget to update the configuration of both clients so that they can communicate with the domains._

**Answer:**

- Screenshot

	![image](https://github.com/user-attachments/assets/a20f74ef-ceeb-4b27-a2a9-f90aa068adc1)


- Explanation
  1. Membuat folder jarkom untuk menyimpan semua konfigurasi : ```mkdir /etc/bind/jarkom```
  2. Melakukan konfigurasi pada setiap web server melalui sebuah script sehinggga konfigurasi bisa tersimpan
		```
		cp /etc/bind/db.local /etc/bind/jarkom/bayam.a07.com
		echo -e '
		; BIND data file for local loopback interface
		;
		$TTL    604800
		@       IN      SOA    bayam.a07.com. root.bayam.a07.com. (
		                        2024100601      ; Serial
		                         604800         ; Refresh
		                          86400         ; Retry
		                        2419200         ; Expire
		                         604800 )       ; Negative Cache TTL
		;
		@       IN      NS      bayam.a07.com.
		@       IN      A       10.8.2.2   ; IP BayamWebServer' > /etc/bind/jarkom/bayam.a07.com
		
		cp /etc/bind/db.local /etc/bind/jarkom/brokoli.a07.com
		echo -e '
		; BIND data file for local loopback interface
		;
		$TTL    604800
		@       IN      SOA   brokoli.a07.com. root.brokoli.a07.com. (
		                        2024100601      ; Serial
		                         604800         ; Refresh
		                          86400         ; Retry
		                        2419200         ; Expire
		                         604800 )       ; Negative Cache TTL
		;
		@       IN      NS     brokoli.a07.com.
		@       IN      A       10.8.2.4   ; IP BrokoliWebServer'> /etc/bind/jarkom/brokoli.a07.com
		
		cp /etc/bind/db.local /etc/bind/jarkom/buncis.a07.com
		echo -e '
		; BIND data file for local loopback interface
		;
		$TTL    604800
		@       IN      SOA   buncis.a07.com. root.buncis.a07.com. (
		                        2024100601      ; Serial
		                         604800         ; Refresh
		                          86400         ; Retry
		                        2419200         ; Expire
		                         604800 )       ; Negative Cache TTL
		;
		@       IN      NS     buncis.a07.com.
		@       IN      A       10.8.2.3; IP BuncisWebServer' >  /etc/bind/jarkom/buncis.a07.com
		```
  3. Membuat domain pada setiap web server
		```
		echo -e '
		zone "bayam.a07.com" {
			type master;
			file "/etc/bind/jarkom/bayam.a07.com";
		};
		
		zone "brokoli.a07.com" {
			type master;
			file "/etc/bind/jarkom/brokoli.a07.com";
		};
		
		zone "buncis.a07.com" {
			type master;
			file "/etc/bind/jarkom/buncis.a07.com";
		};'> /etc/bind/named.conf.local
		
		service bind9 restart
		```
<br>

## Soal 3

> Tambahkan domain alias berupa www.bayam.yyy.com pada alamat bayam.yyy.com dan www.brokoli.yyy.com pada alamat brokoli.yyy.com.

> _Add a domain alias in the form of www.bayam.yyy.com to the bayam.yyy.com address and www.brokoli.yyy.com to the brokoli.yyy.com address._

**Answer:**

- Screenshot
	![image](https://github.com/user-attachments/assets/06cfec92-5b0b-4da5-b834-60b566c0d588)


- Explanation
  	1. Menambahkan tiga zona DNS
		```
	 	echo -e '
		zone "bayam.a07.com" {
			type master;
			file "/etc/bind/jarkom/bayam.a07.com";
		};
		
		zone "brokoli.a07.com" {
			type master;
			file "/etc/bind/jarkom/brokoli.a07.com";
		};'> /etc/bind/named.conf.local
		```
  	2. Melakukan konfigurasi pada setiap web server dan menambahkan nama alias menggunakan `cname`

	 	```
	  	www       IN      CNAME    brokoli.a07.com.
	  	```
	 	```
		www       IN      CNAME    bayam.a07.com.
		```
	<br>

## Soal 4

> Tambahkan record reverse domain untuk domain brokoli.yyy.com dan buncis.yyy.com.

> _Add a reverse domain record for brokoli.yyy.com and buncis.yyy.com domains._

**Answer:**

- Screenshot

  ![image](https://github.com/user-attachments/assets/1eaa07ac-d287-47e3-a065-633e9e0912df)


- Explanation

  1. Menambahkan Konfigurasi Zona Reverse ke File `named.conf.local`
     Zona reverse yang digunakan berada di IP `10.8.2` sehingga direverse menjadi `2.8.10`
		```
		echo -e '
		zone "2.8.10.in-addr.arpa" {
		    type master;
		    file "/etc/bind/jarkom/2.8.10.in-addr.arpa";
		};' >> /etc/bind/named.conf.local
  		```
  2. Menambahkan konfigurasi untuk zona reverse DNS yaitu `2.8.10.in-addr.arpa` ke dalam file konfigurasi `BIND named.conf.local.`

		```
		cp /etc/bind/db.local /etc/bind/jarkom/2.8.10.in-addr.arpa
		echo -e '
		;
		; BIND data file for local loopback interface
		;
		$TTL    604800
		@       IN      SOA     wortel.a07.com. root.wortel.a07.com. (
		                        2024100601      ; Serial
		                         604800         ; Refresh
		                          86400         ; Retry
		                        2419200         ; Expire
		                         604800 )       ; Negative Cache TTL
		;
		2.8.10.in-addr.arpa.    IN      NS      wortel.a07.com.
		3                       IN      PTR     buncis.a07.com. ; byte ke-4 buncis
		4                       IN      PTR     brokoli.a07.com. ; byte ke-4 brokoli' >> /etc/bind/jarkom/2.8.10.in-addr.arpa
		```
	

<br>

## Soal 5

> Ubah record SOA dari domain bayam.yyy.com sesuai dengan ketentuan berikut:
> - Lama waktu server slave menunggu untuk mengecek salinan baru server master adalah sebesar 2 jam.
> - Field yang mengatur revisi file zona ini diubah menjadi tanggal awal praktikum (format YYYYMMDD) kemudian diikuti dengan nomor kelompok (contoh untuk kelompok A02 maka nomornya 02).
> - Lamanya waktu server harus menunggu untuk meminta pembaruan lagi dari nameserver master yang tidak responsif sebesar 30 menit.
> - Lama waktu nama domain di-cache secara lokal sebelum kadaluarsa dan kembali ke nameserver otoritatif untuk informasi terbaru sebesar 12 jam.
> - Jika server slave tidak mendapatkan respons dari server master dalam waktu 2 minggu, server tersebut harus berhenti merespons kueri untuk zona tersebut.

> _Change the SOA record of the bayam.yyy.com domain according to the following conditions:_
> - The length of time the slave server waits to check for a new revision of the master server is 2 hours.
> - The field that regulates the revision of this zone file is changed to the start date of the practicum (YYYYMMDD format) then followed by the group number (ex: for A02 the group number would be 02).
> - The length of time the server has to wait to request another update from an unresponsive master nameserver is 30 minutes.
> - The length of time a domain name is cached locally before it expires and returns to an authoritative nameserver for up-to-date information is 12 hours.
> - If the slave server does not get a response from the master server within 2 weeks, it must stop responding to queries for that zone.

**Answer:**

- Screenshot

  ![image](https://github.com/user-attachments/assets/eae6df39-b641-4695-8d16-c6843f67dd9e)


- Explanation
1. Pada node `WortelDNSMaster` akses file `BIND zone` bayam.a07.com
	`nano /etc/bind/zones/bayam.a07.com`
2. Mengubah Record SOA
   Menyesuaikan record SOA dengan soal yang diminta
   ```
   $TTL    43200 ; 12 jam
	@       IN      SOA     ns1.yyy.com. admin.yyy.com. (
	                        2024100107     ; Serial (2024-10-01-a07)
	                        7200        ; Refresh (2 jam dalam detik)
	                        1800        ; Retry (30 menit dalam detik)
	                        1209600     ; Expire (2 minggu dalam detik)
	                        43200       ; Negative Cache TTL (12 jam dalam detik)
	)

   ```
3. Mengecek hasil `named-checkzone bayam.a07.com /etc/bind/jarkom/bayam.a07.com`


<br>

## Soal 6

> Untuk menangani request yang berlebih dari client ke ketiga alamat yang tadi dibuat, konfigurasikan node Pokcoy sebagai DNS Slave yang bekerja untuk DNS Master Wortel.

> _To handle excess requests from the client to the three addresses created, configure the Pokcoy node as the DNS Slave that works for Wortel DNS Master._

**Answer:**

- Screenshot

  	![image](https://github.com/user-attachments/assets/34fb4764-92ba-4d3c-aa1e-86f945acbf17)


- Explanation
melakukan konfigurasi zona pada wortelDNSMaster
```
echo -e '
zone "bayam.a07.com" {
        type master;
        also-notify { 10.8.2.5; };     //ip pokcoy dnsslave        
        allow-transfer { 10.8.2.5; };  //ip pokcoy dnsslave          
        file "/etc/bind/jarkom/bayam.a07.com";
};

zone "buncis.a07.com" {
        type master;
        also-notify { 10.8.2.5; };   //ip pokcoy dnsslave        
        allow-transfer { 10.8.2.5; };  //ip pokcoy dnsslave                       
        file "/etc/bind/jarkom/buncis.a07.com";
};
zone "brokoli.a07.com" {
        type master;
        also-notify { 10.8.2.5; };      //ip pokcoy dnsslave        
        allow-transfer { 10.8.2.5; };  //ip pokcoy dnsslave            
        file "/etc/bind/jarkom/brokoli.a07.com";
};

zone "10.8.2.in-addr.arpa" {
    type master;
    file "/etc/bind/jarkom/10.8.2.in-addr.arpa";
};' > /etc/bind/named.conf.local
```

melakukan konfigurasi zona pada pokcoyDNSSlave
```
echo -e '
zone "bayam.a07.com" {
    type slave;
    masters { 10.8.3.2; }; // Masukan IP WortelDNSMaster
    file "/var/lib/bind/bayam.a07.com";
};

zone "brokoli.a07.com" {
    type slave;
    masters { 10.8.3.2; }; // Masukan IP WortelDNSMaster
    file "/var/lib/bind/brokoli.a07.com";
};

zone "buncis.a07.com" {
    type slave;
    masters { 10.8.3.2; }; // Masukan IP WortelDNSMaster
    file "/var/lib/bind/buncis.a07.com";
};' > /etc/bind/named.conf.local
```
**Cara Testing**
1. Di PokcoyDNSSlave run script
2. Testing ping di client
   ```
	ping bayam.a07.com
	ping brokoli.a07.com
	ping buncis.a07.com
   ```

<br>

## Soal 7

> Karena membutuhkan tempat untuk menyimpan resep brokoli, buatlah subdomain berupa vitamin.brokoli.yyy.com dengan alias www.vitamin.brokoli.yyy.com dengan mendelegasikannya dari Wortel ke Pokcoy dengan alamat IP menuju Brokoli yang diatur di folder Vitamin.

> _Since we need a place to store Brokoli recipes, create a subdomain in the form of vitamin.brokoli.yyy.com with an alias of www.vitamin.brokoli.yyy.com by delegating it from Wortel to Pokcoy with an ip to the Brokoli node in a folder called Vitamin._

**Answer:**

- Screenshot

	![image (1)](https://github.com/user-attachments/assets/cfae0d41-20ca-433d-8fe2-bf7befa675eb)

- Explanation

 melakukan konfigurasi zona DNS untuk brokoli.a07.com pada wortelDNSMaster `brokoli.a07.com-7`
 ```
 echo -e ';
; BIND data file for local loopback interface
;
$TTL    604800
@       IN      SOA     brokoli.a07.com. root.brokoli.a07.com. (
                        2024100601      ; Serial
                         604800         ; Refresh
                          86400         ; Retry
                        2419200         ; Expire
                         604800 )       ; Negative Cache TTL
;
@       IN      NS      brokoli.a07.com.
@       IN      A       10.8.2.4   ; IP brokoli
www     IN      CNAME   brokoli.a07.com.
ns1     IN      A       10.8.2.5   ; IP pokcoy
vitamin     IN      NS      ns1' > /etc/bind/jarkom/brokoli.a07.com
```

lalu melakukan konfigurasi forwarder opsi global untuk BIND DNS pada wortelDNSMaster `cat named.conf.options-7`
```
echo -e 'options {
        directory "/var/cache/bind";

        // If there is a firewall between you and nameservers you want
        // to talk to, you may need to fix the firewall to allow multiple
        // ports to talk.  See http://www.kb.cert.org/vuls/id/800113

        // If your ISP provided one or more IP addresses for stable 
        // nameservers, you probably want to use them as forwarders.  
        // Uncomment the following block, and insert the addresses replacing 
        // the all-0s placeholder.

        // forwarders {
        //      0.0.0.0;
        // };

        //========================================================================
        // If BIND logs error messages about the root key being expired,
        // you will need to update your keys.  See https://www.isc.org/bind-keys
        //========================================================================
        //dnssec-validation auto;
        allow-query{any;};

        auth-nxdomain no;    # conform to RFC1035
        listen-on-v6 { any; };
};' > /etc/bind/named.conf.options
service bind9 restart
```

melakukan konfigurasi opsi global untuk BIND DNS pada pokcoyDNSSlave `cat named.conf.options-7`
```
	echo -e 'options {
	        directory "/var/cache/bind";
	
	        // If there is a firewall between you and nameservers you want
	        // to talk to, you may need to fix the firewall to allow multiple
	        // ports to talk.  See http://www.kb.cert.org/vuls/id/800113
	
	        // If your ISP provided one or more IP addresses for stable 
	        // nameservers, you probably want to use them as forwarders.  
	        // Uncomment the following block, and insert the addresses replacing 
	        // the all-0s placeholder.
	
	        // forwarders {
	        //      0.0.0.0;
	        // };
	
	        //========================================================================
	        // If BIND logs error messages about the root key being expired,
	        // you will need to update your keys.  See https://www.isc.org/bind-keys
	        //========================================================================
	        //dnssec-validation auto;
	        allow-query{any;};
	        
	        auth-nxdomain no;    # conform to RFC1035
	        listen-on-v6 { any; };
	};' > /etc/bind/named.conf.options
	
	echo -e 'zone "vitamin.brokoli.a07.com" {
	    type master;
	    file "/etc/bind/vitamin/vitamin.brokoli.a07.com";
	};' >> /etc/bind/named.conf.local
```
melakukan konfigurasi zona DNS untuk brokoli.a07.com pada pokcoyDNSSlave
```	
	mkdir /etc/bind/vitamin
	
	cp /etc/bind/db.local /etc/bind/vitamin/vitamin.brokoli.a07.com
	
	echo -e ';
	; BIND data file for local loopback interface
	;
	$TTL    604800
	@       IN      SOA     vitamin.brokoli.a07.com. root.vitamin.brokoli.a07.com. (
	                        2024100601      ; Serial
	                         604800         ; Refresh
	                          86400         ; Retry
	                        2419200         ; Expire
	                         604800 )       ; Negative Cache TTL
	;
	@       IN      NS      vitamin.brokoli.a07.com.
	@       IN      A       10.8.2.4  ; IP Brokoli
	www     IN      CNAME   vitamin.brokoli.a07.com.' > /etc/bind/vitamin/vitamin.brokoli.a07.com
	service bind9 restart
 ```
**Testing**
* Di client
```
ping www.vitamin.brokoli.a07.com
```
<br>

## Soal 8

> Buatlah subdomain khusus untuk kandungan brokoli dengan akses k1.vitamin.brokoli.yyy.com dengan alias www.k1.vitamin.brokoli.yyy.com yang mengarah ke IP brokoli dan diatur di folder k1.  

> _Create a special subdomain for Brokoli content called k1.vitamin.brokoli.yyy.com with an alias called www.k1.vitamin.brokoli.yyy.com that point to Brokoli node and are organized in a folder called k1._

**Answer:**

- Screenshot

 	![image (2)](https://github.com/user-attachments/assets/dd194195-ac4e-4de4-ac03-520b64349f3f)


- Explanation

  melakukan  penambahan zona untuk k1.vitamin.brokoli.a07.com di named.conf.local pada slave `named.conf.local-8` dan membuat konfigurasi BIND `k1.vitamin.brokoli.a07.com-8`
```
  echo -e 'zone "k1.vitamin.brokoli.a07.com" {
    type master;
    file "/etc/bind/k1/k1.vitamin.brokoli.a07.com";
};' >> /etc/bind/named.conf.local

mkdir /etc/bind/k1

cp /etc/bind/db.local /etc/bind/k1/k1.vitamin.brokoli.a07.com

echo -e ';
; BIND data file for local loopback interface
;
$TTL    604800
@       IN      SOA     k1.vitamin.brokoli.a07.com. root.k1.vitamin.brokoli.a07.com. (
                        2024100601      ; Serial
                         604800         ; Refresh
                          86400         ; Retry
                        2419200         ; Expire
                         604800 )       ; Negative Cache TTL
;
@       IN      NS      k1.vitamin.brokoli.a07.com.
@       IN      A       10.8.2.4  ; IP Brokoli
www     IN      CNAME   k1.vitamin.brokoli.a07.com.' > /etc/bind/k1/k1.vitamin.brokoli.a07.com
service bind9 restart
```
**Testing**
* Di client
  ```
  ping www.k1.vitamin.brokoli.a07.com
  ```
<br>

## Soal 9

> Bayam, Brokoli, dan Buncis masing-masing berfungsi sebagai web server nginx yang menyajikan resep khusus untuk jenis sayuran yang mereka tangani. Untuk mengaktifkan web server pada masing-masing worker, lakukan deployment website menggunakan sumber yang tersedia di sayur_webserver_nginx. Tambahkan konfigurasi untuk log error ke file /var/log/nginx/error.log dan log access ke file /var/log/nginx/access.log.

> _Bayam, Brokoli, and Buncis each function as nginx web servers that serve special recipes for the type of vegetables they handle. To activate the web server on each worker, do the deployment using the resources available in sayur_webserver_nginx. Add configuration for error log to the file /var/log/nginx/error.log and access log to the file /var/log/nginx/access.log._

**Answer:**

- Screenshot

  	![image](https://github.com/user-attachments/assets/44b4726c-866e-4c13-8463-ea2903785feb)


- Explanation
  Dikerjakan menggunakan script berikut
  	```
	apt-get update 
	apt install nginx php php-fpm -y
	
	mkdir -p /var/www/jarkom
	
	echo -e '<?php
	$hostname = gethostname();
	$date = date("l, d F Y H:i:s");
	$php_version = phpversion();
	$visitor_ip = $_SERVER['REMOTE_ADDR'];
	
	echo "<h1>Selamat Datang di Situs Resep Sayuran!</h1>";
	echo "<p>Pengunjung dari IP: <strong>$visitor_ip</strong></p>";
	echo "<p>Versi PHP: <strong>$php_version</strong></p>";
	echo "<p>Waktu: <strong>$date</strong></p>";
	echo "<hr>";
	echo "<p>Saat ini Anda sedang mengakses resep dari sayur: <strong>$hostname</strong></p>";
	
	switch ($hostname) {
	    case 'Bayam':
	        if (!@include 'resep_1.php') {
	            echo "<p>Gagal Memuat Resep! Cek Error Log untuk info lebih lanjut.</p>";
	            error_log("File resep_1.php tidak ditemukan!\n", 3, "/var/log/nginx/error.log");
	        }
	        break;
	    case 'Buncis':
	        if (!@include 'resep_2.php') {
	            echo "<p>Gagal Memuat Resep! Cek Error Log untuk info lebih lanjut.</p>";
	            error_log("File resep_2.php tidak ditemukan!\n", 3, "/var/log/nginx/error.log");
	        }
	        break;
	    case 'Brokoli':
	        if (!@include 'resep_3.php') {
	            echo "<p>Gagal Memuat Resep! Cek Error Log untuk info lebih lanjut.</p>";
	            error_log("File resep_3.php tidak ditemukan!\n", 3, "/var/log/nginx/error.log");
	        }
	        break;
	    default:
	        echo "<p>Gagal Memuat Resep! Cek Error Log untuk info lebih lanjut.</p>";
	        error_log("Hostname tidak ditemukan!\n", 3, "/var/log/nginx/error.log");
	        break;
	}
	?>' > /var/www/jarkom/index.php
	
	echo -e '<?php
	echo "<h2>Resep Spesial: Tumis Bayam Bawang Putih</h2>";
	echo "<p>Bahan:</p>";
	echo "<ul>";
	echo "<li>Bayam segar 200 gram</li>";
	echo "<li>Bawang putih 3 siung</li>";
	echo "<li>Garam dan merica secukupnya</li>";
	echo "<li>Minyak untuk menumis</li>";
	echo "</ul>";
	echo "<p>Cara Memasak:</p>";
	echo "<ol>";
	echo "<li>Cuci bersih bayam dan tiriskan.</li>";
	echo "<li>Iris tipis bawang putih.</li>";
	echo "<li>Tumis bawang putih hingga harum.</li>";
	echo "<li>Masukkan bayam, aduk hingga layu.</li>";
	echo "<li>Bumbui dengan garam dan merica.</li>";
	echo "<li>Sajikan selagi hangat.</li>";
	echo "</ol>";
	?>
	' > /var/www/jarkom/resep1.php
	
	echo -e '<?php
	echo "<h2>Resep Spesial: Buncis Goreng Tepung Renyah</h2>";
	echo "<p>Bahan:</p>";
	echo "<ul>";
	echo "<li>Buncis muda 250 gram</li>";
	echo "<li>Tepung terigu 100 gram</li>";
	echo "<li>Tepung beras 50 gram</li>";
	echo "<li>Air es 150 ml</li>";
	echo "<li>Garam dan bubuk bawang putih</li>";
	echo "<li>Minyak untuk menggoreng</li>";
	echo "</ul>";
	echo "<p>Cara Memasak:</p>";
	echo "<ol>";
	echo "<li>Cuci bersih buncis dan potong ujungnya.</li>";
	echo "<li>Campur tepung terigu, tepung beras, garam, dan bubuk bawang putih.</li>";
	echo "<li>Tambahkan air es sedikit demi sedikit hingga adonan kental.</li>";
	echo "<li>Celupkan buncis ke dalam adonan.</li>";
	echo "<li>Goreng dalam minyak panas hingga keemasan.</li>";
	echo "<li>Tiriskan dan sajikan dengan saus.</li>";
	echo "</ol>";
	?>
	' > /var/www/jarkom/resep2.php
	
	echo -e '<?php
	echo "<h2>Resep Spesial: Sup Brokoli Keju Lezat</h2>";
	echo "<p>Bahan:</p>";
	echo "<ul>";
	echo "<li>Brokoli 200 gram</li>";
	echo "<li>Keju cheddar parut 50 gram</li>";
	echo "<li>Susu cair 200 ml</li>";
	echo "<li>Bawang bombay cincang 1/2 buah</li>";
	echo "<li>Garam, merica, dan pala bubuk secukupnya</li>";
	echo "<li>Margarin untuk menumis</li>";
	echo "</ul>";
	echo "<p>Cara Memasak:</p>";
	echo "<ol>";
	echo "<li>Tumis bawang bombay dengan margarin hingga harum.</li>";
	echo "<li>Tambahkan brokoli, masak sebentar.</li>";
	echo "<li>Tuang susu cair, masak hingga brokoli empuk.</li>";
	echo "<li>Bumbui dengan garam, merica, dan pala bubuk.</li>";
	echo "<li>Tambahkan keju parut, aduk hingga meleleh.</li>";
	echo "<li>Sajikan hangat.</li>";
	echo "</ol>";
	?>
	' > /var/www/jarkom/resep3.php
	
	
	echo -e 'server {

        listen 80;

        root /var/www/jarkom;

        index index.php index.html index.htm;
        server_name _;

        location / {
                try_files $uri $uri/ /index.php?$query_string;
        }

        # pass PHP scripts to FastCGI server
        location ~ \.php$ {
                include snippets/fastcgi-php.conf;
                fastcgi_pass unix:/var/run/php/php7.2-fpm.sock;
        }

        location ~ /\.ht {
                deny all;
                }

                error_log /var/log/nginx/error.log;
                access_log /var/log/nginx/access.log;
	}' > /etc/nginx/sites-available/default
	
	service php7.2-fpm start
	service nginx restart
	```

<br>

## Soal 10

> Pada masing masing worker nginx, akan terdapat beberapa hal yang perlu diperbaiki pada resource yang diberikan untuk bisa menampilkan resep saat halaman dimuat. Analisis kesalahan yang ada di resource melalui file /var/log/nginx/error.log dan perbaiki hingga halaman bisa menampilkan resep sesuai dengan worker nya.

> _On each nginx worker, there will be several things that need to be fixed in the resources provided to be able to display recipes when the page is loaded. Analyze the errors in the resource through the /var/log/nginx/error.log file and fix it until the page can display recipes according to its worker._

**Answer:**

- Screenshot

  ![image](https://github.com/user-attachments/assets/398fbdfa-ea8a-44fd-a499-c00beba56042)


- Explanation

  `Put your explanation in here`

<br>

## Soal 11

> Setelah website berhasil dideploy pada masing-masing worker (Bayam, Brokoli, dan Buncis) dan halaman dapat menampilkan resep sayuran yang sesuai,  buatlah custom access log ke file /var/log/nginx/access.log di masing-masing web server worker menggunakan format log tertentu seperti di bawah:
> - Tanggal dan waktu akses dalam format standar log.
Nama worker yang sedang dilayani (misalnya: Bayam, Brokoli, atau Buncis).
> - Alamat IP klien yang mengakses website.
> - Metode HTTP dan URI yang diakses oleh klien.
> - Status respons HTTP yang diberikan oleh server.
> - Jumlah byte yang dikirimkan dalam respons.
> - Waktu yang dihabiskan oleh server untuk menangani permintaan.
> <br> </br>
> Contoh format log yang sesuai: 
[01/Oct/2024:11:30:45 +0000] Jarkom Node Bayam Access from 192.168.1.15 using method "GET /resep/bayam HTTP/1.1" returned stat


> _After successfully deploying the website on each worker (Bayam, Brokoli, and Buncis) and ensuring the pages display the appropriate vegetable recipes, create a custom access log file at /var/log/nginx/access.log on each web server worker using a specific log format as described below:_
> - _Access date and time in standard log format._
> - _Name of the worker serving the request (e.g., Bayam, Brokoli, or Buncis)._
> - _Client IP address accessing the website._
> - _HTTP method and URI accessed by the client._
> - _HTTP response status provided by the server.__
> - _Number of bytes sent in the response.
> - _Time taken by the server to handle the request._
> <br> </br>
> _Example of the appropriate log format:
[01/Oct/2024:11:30:45 +0000] Jarkom Node Bayam Access from 192.168.1.15 using method "GET /resep/bayam HTTP/1.1" returned status 200 with 2567 bytes sent in 0.038 seconds_


**Answer:**

- Screenshot

  	![image](https://github.com/user-attachments/assets/1befd4e3-9d33-40de-8a7a-63fcc0d103f5)


- Explanation
  	Akses nano /etc/nginx/nginx.conf, lalu tambahkan berikut di http { }
	 ```
		log_format custom_access '[$time_local] Jarkom Node $hostname Access from $remote_addr '
	                             'using method "$request_method $request_uri HTTP/$server_protocol" '
	                             'returned status $status with $body_bytes_sent bytes sent in $request_time seconds';
	
	    access_log /var/log/nginx/access.log custom_access;  # Simpan akses log dengan format kustom
	
	    # Pastikan untuk menyertakan file konfigurasi server di sini
	    include /etc/nginx/sites-enabled/*;
	  ```

<br>

## Soal 12

> Informasi vitamin pada sayur brokoli akan ditampilkan pada subdomain vitamin.brokoli.yyy.com di node brokoli, buatlah DocumentRoot yang disimpan pada /var/www/vitamin.brokoli.yyy. Konfigurasikan webserver dengan nama server vitamin.brokoli.yyy.com dan server alias www.vitamin.brokoli.yyy.com. Lakukan konfigurasi Apache Web Server pada Brokoli dengan menggunakan sumber yang tersedia di [sini](https://docs.google.com/uc?export=download&id=1QbGkKXo3jt4c68AdVAkl1hD4LolTUPg2).

> _For information on vitamins in brokoli will be displayed on the vitamin.brokoli.yyy.com subdomain on the brokoli node, create a DocumentRoot stored in /var/www/vitamin.brokoli.yyy. Configure the web server with the server name vitamin.brokoli.yyy.com and server alias www.vitamin.brokoli.yyy.com. Configure the Apache Web Server on Brokoli using [this resource](https://docs.google.com/uc?export=download&id=1QbGkKXo3jt4c68AdVAkl1hD4LolTUPg2)._

**Answer:**

- Screenshot

   ![image](https://github.com/user-attachments/assets/f833c566-f4b7-4cb3-bf10-e9100e717ea3)

- Explanation
	

	dilakukan wget untuk melakukan download zip yang dilanjutkan unzip
	![image](https://github.com/user-attachments/assets/5c0cfd05-c678-4641-a76b-1e6cf64c94d9)
	dan dilakukan perubahan oada sites-available/default pada nginx
	![image](https://github.com/user-attachments/assets/ac8d15ac-8f7d-4517-b959-325ee7256f5f)
	![image](https://github.com/user-attachments/assets/c3c860f4-e117-4d66-9401-a4d745cb5b96)

	dan sites-available/default-8080.conf
	![image](https://github.com/user-attachments/assets/15690a2c-0b2d-4288-b44f-e1a5bf04f408)

	lalu pada apavhe2/ports.conf
	![image](https://github.com/user-attachments/assets/4b23b248-26e2-47c9-9de7-e0aa3e013d0e)

<br>

## Soal 13

> Pada subdomain vitamin.brokoli.yyy.com, terdapat subfolder /nutrisi yang menyediakan informasi tentang berbagai vitamin dalam brokoli, seperti Vitamin A, C, dan K. Aktifkan directory listing untuk folder /nutrisi, dan buatlah rewrite rule di Apache untuk memperbaiki URL agar halaman seperti www.vitamin.brokoli.yyy.com/nutrisi/vitamin_a.php dapat diakses hanya dengan www.vitamin.brokoli.yyy.com/nutrisi/vitamin_a. Pastikan setiap halaman vitamin dapat diakses langsung melalui url yang telah disederhanakan.

> _On the vitamin.brokoli.yyy.com subdomain, there is a /nutrisi subfolder that provides information about various vitamins in brokoli, such as Vitamin A, C, and K. Activate directory listing for the /nutrisi folder, and create a rewrite rule in Apache to fix the URL so that pages like www.vitamin.brokoli.yyy.com/nutrisi/vitamin_a.php can be accessed only with www.vitamin.brokoli.yyy.com/nutrisi/vitamin_a. Make sure each vitamin page can be accessed directly through the simplified url._

**Answer:**

- Screenshot

  ![image](https://github.com/user-attachments/assets/5e94369f-964d-465d-9edf-e57d54a5fee7)


- Explanation

  dilakukan perubahan pada default-8080.conf
  	![image](https://github.com/user-attachments/assets/16ccebf8-9b18-438a-b82c-c98088ba3d83)
	![image](https://github.com/user-attachments/assets/2f39eca5-0b98-494f-b24a-820d541e5595)
 serta penyesuaian pada /var/www/vitamin.brokoli.a07/nutrisi/.htaccess
	![image](https://github.com/user-attachments/assets/7b5c1eb1-9239-4339-9ec4-4aeb8f7941e7)



<br>

## Soal 14

> Tambahkan alias untuk folder /public/images/ pada subdomain www.vitamin.brokoli.yyy.com agar folder tersebut dapat diakses langsung melalui url www.vitamin.brokoli.yyy.com/img.

> _Add an alias for the /public/images/ folder on the www.vitamin.brokoli.yyy.com subdomain so that the folder can be accessed directly through the url www.vitamin.brokoli.yyy.com/img._

**Answer:**

- Screenshot

 ![image](https://github.com/user-attachments/assets/d49eede6-b694-4f3b-90eb-4e574c3c5ae6)


- Explanation
dilakukan perubahan pada default-8080.conf
  	![image](https://github.com/user-attachments/assets/3f0deb5d-219b-43f4-b7eb-c3ef453ec97c)
	![image](https://github.com/user-attachments/assets/01b3be04-2429-4565-bb3e-a82d240245f3)

<br>

## Soal 15

> Karena terdapat resep rahasia di file /secret/recipe_secret.txt pada subdomain www.vitamin.brokoli.yyy.com, konfigurasikan folder /secret agar tidak dapat diakses oleh pengguna (dengan menampilkan 403 Forbidden).

> _Because there is a secret recipe in the /secret/recipe_secret.txt file on the www.vitamin.brokoli.yyy.com subdomain, configure the /secret folder so that it cannot be accessed by users (by displaying 403 Forbidden)._

**Answer:**

- Screenshot

 ![image](https://github.com/user-attachments/assets/013496b1-2d97-465e-a20d-b037488f39b1)


- Explanation

 	dilakukan perubahan pada default-8080.conf
	![image](https://github.com/user-attachments/assets/99832f91-d708-4f25-9d3e-86baec9b9aa7)
	![image](https://github.com/user-attachments/assets/e90bbf28-cd77-452c-8665-19e9fefb0a0d)

<br>

## Soal 16

> Karena dinilai terlalu panjang coba ubah konfigurasi www.vitamin.brokoli.yyy.com/public/js menjadi www.vitamin.brokoli.yyy.com/js

> _Since it is considered too long, change the configuration from www.vitamin.brokoli.yyy.com/public/js to www.vitamin.brokoli.yyy.com/js._

**Answer:**

- Screenshot

 ![image](https://github.com/user-attachments/assets/8899bf52-a384-4976-a139-7e85df774a07)


- Explanation

  dilakukan perubahan pada default-8080.conf
  	![image](https://github.com/user-attachments/assets/4a580841-755f-4ea1-82e2-2589718fd356)
	![image](https://github.com/user-attachments/assets/cbb311c2-72e3-4a4a-8709-0ea16a0181ae)


<br>

## Soal 17

> Supaya Web kita aman terkendali maka ubah konfigurasi www.k1.vitamin.brokoli.yyy.com menjadi hanya bisa di akses oleh port 9696 dan 8888

> _To keep our web secure, configure www.k1.vitamin.brokoli.yyy.com to only be accessible through ports 9696 and 8888._

**Answer:**

- Screenshot

 
![image](https://github.com/user-attachments/assets/b8d57611-39fb-4a0c-8fc9-a11e062ee8f4)


- Explanation

  dilakukan perubahan pada default-8080-2.conf
	![image](https://github.com/user-attachments/assets/bb2f0f9c-8985-4bed-a536-237697c7323b)
	![image](https://github.com/user-attachments/assets/5581dade-ba78-41ca-ba97-3bdc1eea5c9f)
	![image](https://github.com/user-attachments/assets/39eade11-e45e-4ff7-9772-16bf24103383)
	dan perubahan pada nginx/sites-available di kedua port 9696 dan 8888
	![image](https://github.com/user-attachments/assets/a9e9ddc1-0662-4afb-bab9-de60f16f26ce)
	![image](https://github.com/user-attachments/assets/bae3bee4-09c0-49d5-a67f-c328f02984f9)
	dan pada apache2/ports.conf
	![image](https://github.com/user-attachments/assets/9719f5cd-3ce4-4222-a692-f5a59acac74e)

<br>

## Soal 18

> Lanjutkan dari nomor sebelumnya buatlah autentikasi dengan username “Seblak” dan password “sehatyyy” dengan yyy adalah kode kelompok. Letakkan Document Root pada /var/www/k1.vitamin.brokoli.yyy.

> _Continuing from the previous point, create authentication with the username “Seblak” and the password “sehatyyy” where yyy is the group code. Set the Document Root to /var/www/k1.vitamin.brokoli.yyy._

**Answer:**

- Screenshot

  ![image](https://github.com/user-attachments/assets/1d3038b6-686c-4e51-b87f-c4902709370b)


- Explanation
dilakukan perubahan pada default-8080-2.conf pada kedua port yang dituju
![image](https://github.com/user-attachments/assets/c148ef45-a1f0-41dc-a450-bbfedf481cac)

  
  

<br>

## Soal 19

> Konfigurasikan agar setiap kali IP Brokoli diakses dengan lynx, secara otomatis akan dialihkan ke www.brokoli.yyy.com (alias).

> _Configure it so that every time Brokoli's IP is accessed using lynx, it is automatically redirected to www.brokoli.yyy.com (alias)._

**Answer:**

- Screenshot

  `![image](https://github.com/user-attachments/assets/a70577a6-27ee-445f-b600-b6efd2847c99)


- Explanation

 dilakukan perubahan pada nginx/sites-available/default
 ![image](https://github.com/user-attachments/assets/5d3f22fc-1b79-4cda-bcf6-326daf13058f)
![image](https://github.com/user-attachments/assets/41dbdbbc-fce4-424d-b7e7-1357994ddfba)
![image](https://github.com/user-attachments/assets/8be644d6-edb2-4163-95fd-0cfa4d401b22)
![image](https://github.com/user-attachments/assets/4508f0d2-3ffb-4879-acac-be396b2e2df6)


<br>

## Soal 20

> Karena jumlah pengunjung website www.vitamin.brokoli.yyy.com semakin meningkat dan terdapat banyak gambar random, ubah permintaan gambar yang mengandung substring "vitamin" agar diarahkan ke file vitamin.png.

> _Since the number of visitors to www.vitamin.brokoli.yyy.com is increasing and there are many random images, redirect image requests that contain the substring "vitamin" to the file vitamin.png._

**Answer:**

- Screenshot

  ![image](https://github.com/user-attachments/assets/aeb3bca9-e07a-464c-9af0-24fc29e0740c)


- Explanation
	dilakukan perubahan pada default-8080-2.conf
	![image](https://github.com/user-attachments/assets/6c766aa9-29b7-4af9-80f3-b41eb9080d4e)


<br>
  
## Problems
itu, sakit perut
## Revisions (if any)
