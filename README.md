# Consulta DNS e Investigación de Dominios

Este documento contén as respostas ás consultas DNS feitas en torno a varios dominios e IPs, seguindo as indicacións proporcionadas.

## 1. Consulta dig danielcastelao.org

A consulta realizada mediante o comando dig danielcastelao.org proporciona a seguinte información:

```bash
dig danielcastelao.org
 DiG 9.18.28-0ubuntu0.22.04.1-Ubuntu <<>> dig danielcastelao.org
;; global options: +cmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: SERVFAIL, id: 5100
;; flags: qr aa rd ra; QUERY: 1, ANSWER: 0, AUTHORITY: 0, ADDITIONAL: 1

;; OPT PSEUDOSECTION:
; EDNS: version: 0, flags:; udp: 65494
;; QUESTION SECTION:
;dig.				IN	A

;; Query time: 0 msec
;; SERVER: 127.0.0.53#53(127.0.0.53) (UDP)
;; WHEN: Mon Oct 21 19:34:16 CEST 2024
;; MSG SIZE  rcvd: 32

;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 64871
;; flags: qr rd ra; QUERY: 1, ANSWER: 1, AUTHORITY: 0, ADDITIONAL: 1

;; OPT PSEUDOSECTION:
; EDNS: version: 0, flags:; udp: 65494
;; QUESTION SECTION:
;danielcastelao.org.		IN	A

;; ANSWER SECTION:
danielcastelao.org.	900	IN	A	178.211.133.37

;; Query time: 131 msec
;; SERVER: 127.0.0.53#53(127.0.0.53) (UDP)
;; WHEN: Mon Oct 21 19:34:17 CEST 2024
;; MSG SIZE  rcvd: 63
```

### Partes da resposta:

- **IN**: Internet, é a clase do rexistro.
- **A**: Rexistro de dirección, que asocia o nome do dominio cunha IP.
- **QUERY SECTION**: A consulta que se fixo, neste caso, `danielcastelao.org` solicitando o rexistro tipo A.
- **ANSWER SECTION**: A resposta, que contén a dirección IP asociada ao dominio.
- **AUTHORITY SECTION**: Lista os servidores de nomes autoritativos para o dominio.
- **QUERY TIME**: O tempo que tardou a consulta.
- **SERVER**: O servidor DNS que respondeu á consulta (neste caso, Google DNS: 8.8.8.8).

## 2. Comparativa entre moodle.danielcastelao.org e www.danielcastelao.org

### Resultado para moodle.danielcastelao.org:
```bash
dig moodle.danielcastelao.org

; <<>> DiG 9.18.28-0ubuntu0.22.04.1-Ubuntu <<>> moodle.danielcastelao.org
;; global options: +cmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NXDOMAIN, id: 6471
;; flags: qr rd ra; QUERY: 1, ANSWER: 0, AUTHORITY: 0, ADDITIONAL: 1

;; OPT PSEUDOSECTION:
; EDNS: version: 0, flags:; udp: 65494
;; QUESTION SECTION:
;moodle.danielcastelao.org.	IN	A

;; Query time: 127 msec
;; SERVER: 127.0.0.53#53(127.0.0.53) (UDP)
;; WHEN: Mon Oct 21 19:49:18 CEST 2024
;; MSG SIZE  rcvd: 54
```

### Resultado danielcastelao.org
```bash
dig www.danielcastelao.org

; <<>> DiG 9.18.28-0ubuntu0.22.04.1-Ubuntu <<>> danielcastelao.com
;; global options: +cmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NXDOMAIN, id: 29966
;; flags: qr rd ra; QUERY: 1, ANSWER: 0, AUTHORITY: 0, ADDITIONAL: 1

;; OPT PSEUDOSECTION:
; EDNS: version: 0, flags:; udp: 65494
;; QUESTION SECTION:
;danielcastelao.com.		IN	A

;; Query time: 40 msec
;; SERVER: 127.0.0.53#53(127.0.0.53) (UDP)
;; WHEN: Mon Oct 21 19:49:24 CEST 2024
;; MSG SIZE  rcvd: 47
```

Ambos dominios teñen a mesma dirección IP. Non hai moitas diferencias na configuración de DNS, o que indica que ambas as dúas URL apuntan ao mesmo servidor.

## 3. Nome e IP dos servidores de DNS autoritativos

Consulta para saber os servidores DNS autoritativos de `www.danielcastelao.org`:
```bash
dig danielcastelao.org SOA

; <<>> DiG 9.18.28-0ubuntu0.22.04.1-Ubuntu <<>> danielcastelao.org SOA
;; global options: +cmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 32414
;; flags: qr rd ra; QUERY: 1, ANSWER: 1, AUTHORITY: 0, ADDITIONAL: 1

;; OPT PSEUDOSECTION:
; EDNS: version: 0, flags:; udp: 65494
;; QUESTION SECTION:
;danielcastelao.org.		IN	SOA

;; ANSWER SECTION:
danielcastelao.org.	900	IN	SOA	ns1.hover.com. dnsmaster.hover.com. 1720467415 1800 900 604800 300

;; Query time: 139 msec
;; **SERVER: 127.0.0.53#53(127.0.0.53) (UDP)**
;; WHEN: Mon Oct 21 19:51:18 CEST 2024
;; MSG SIZE  rcvd: 106
```

### Por que soen ser 2 servidores autoritativos?
É común ter ao menos dous servidores DNS para garantir a redundancia e a dispoñibilidade do servizo en caso de falla dun dos servidores.

## 4. Consulta de nomes inversos

Consulta inversa para `130.206.164.68`:
```bash
dig 130.206.164.68

; <<>> DiG 9.18.28-0ubuntu0.22.04.1-Ubuntu <<>> 130.206.164.68
;; global options: +cmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 58380
;; flags: qr rd ra; QUERY: 1, ANSWER: 1, AUTHORITY: 0, ADDITIONAL: 1

;; OPT PSEUDOSECTION:
; EDNS: version: 0, flags:; udp: 65494
;; QUESTION SECTION:
;130.206.164.68.			IN	A

;; ANSWER SECTION:
130.206.164.68.		0	IN	A	130.206.164.68

;; Query time: 60 msec
;; SERVER: 127.0.0.53#53(127.0.0.53) (UDP)
;; WHEN: Mon Oct 21 19:53:57 CEST 2024
;; MSG SIZE  rcvd: 59
```
## 5. Rexistro www.elpais.com e TTL
```bash
dig www.elpais.com

; <<>> DiG 9.18.28-0ubuntu0.22.04.1-Ubuntu <<>> www.elpais.com
;; global options: +cmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 4610
;; flags: qr rd ra; QUERY: 1, ANSWER: 2, AUTHORITY: 0, ADDITIONAL: 1

;; OPT PSEUDOSECTION:
; EDNS: version: 0, flags:; udp: 65494
;; QUESTION SECTION:
;www.elpais.com.			IN	A

;; ANSWER SECTION:
www.elpais.com.		5	IN	CNAME	prisa-us-eu.map.fastly.net.
prisa-us-eu.map.fastly.net. 25	IN	A	151.101.134.133

;; Query time: 8 msec
;; SERVER: 127.0.0.53#53(127.0.0.53) (UDP)
;; WHEN: Mon Oct 21 19:56:00 CEST 2024
;; MSG SIZE  rcvd: 99
```
###TTL
```bash
dig +noall +answer www.elpais.com
www.elpais.com.		5	IN	CNAME	prisa-us-eu.map.fastly.net.
prisa-us-eu.map.fastly.net. 15	IN	A	151.101.134.133
```


##6. Máquinas detrás de www.google.com

```bash
dig www.google.es

; <<>> DiG 9.18.28-0ubuntu0.22.04.1-Ubuntu <<>> www.google.es
;; global options: +cmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 61597
;; flags: qr rd ra; QUERY: 1, ANSWER: 1, AUTHORITY: 0, ADDITIONAL: 1

;; OPT PSEUDOSECTION:
; EDNS: version: 0, flags:; udp: 65494
;; QUESTION SECTION:
;www.google.es.			IN	A

;; ANSWER SECTION:
www.google.es.		6	IN	A	142.250.200.131

;; Query time: 5 msec
;; SERVER: 127.0.0.53#53(127.0.0.53) (UDP)
;; WHEN: Mon Oct 21 20:02:17 CEST 2024
;; MSG SIZE  rcvd: 58
```
### Normalmente, Google usa balanceo de carga, polo que verás varias IPs que non sempre son as mesmas.


## 7. Pregunta a un servidor raíz

```bash
dig @J.ROOT-SERVERS.NET www.google.es

; <<>> DiG 9.18.28-0ubuntu0.22.04.1-Ubuntu <<>> @J.ROOT-SERVERS.NET www.google.es
; (1 server found)
;; global options: +cmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 19536
;; flags: qr rd; QUERY: 1, ANSWER: 0, AUTHORITY: 4, ADDITIONAL: 9
;; WARNING: recursion requested but not available

;; OPT PSEUDOSECTION:
; EDNS: version: 0, flags:; udp: 1472
;; QUESTION SECTION:
;www.google.es.			IN	A

;; AUTHORITY SECTION:
es.			172800	IN	NS	a.nic.es.
es.			172800	IN	NS	c.nic.es.
es.			172800	IN	NS	g.nic.es.
es.			172800	IN	NS	h.nic.es.

;; ADDITIONAL SECTION:
a.nic.es.		172800	IN	A	194.69.254.1
c.nic.es.		172800	IN	A	194.0.34.53
g.nic.es.		172800	IN	A	204.61.217.1
h.nic.es.		172800	IN	A	194.0.33.53
a.nic.es.		172800	IN	AAAA	2001:67c:21cc:2000::64:41
c.nic.es.		172800	IN	AAAA	2001:678:44::53
g.nic.es.		172800	IN	AAAA	2001:500:14:7001:ad::1
h.nic.es.		172800	IN	AAAA	2001:678:40::53

;; Query time: 52 msec
;; SERVER: 192.58.128.30#53(J.ROOT-SERVERS.NET) (UDP)
;; WHEN: Mon Oct 21 20:03:24 CEST 2024
;; MSG SIZE  rcvd: 286
```

## 8. Servidores de correo danielcastelo.org:
```bash
dig danielcastelao.org MX

; <<>> DiG 9.18.28-0ubuntu0.22.04.1-Ubuntu <<>> danielcastelao.org MX
;; global options: +cmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 23489
;; flags: qr rd ra; QUERY: 1, ANSWER: 7, AUTHORITY: 0, ADDITIONAL: 1

;; OPT PSEUDOSECTION:
; EDNS: version: 0, flags:; udp: 65494
;; QUESTION SECTION:
;danielcastelao.org.		IN	MX

;; ANSWER SECTION:
danielcastelao.org.	900	IN	MX	130 aspmx4.googlemail.com.
danielcastelao.org.	900	IN	MX	100 alt2.aspmx.l.google.com.
danielcastelao.org.	900	IN	MX	120 aspmx3.googlemail.com.
danielcastelao.org.	900	IN	MX	90 alt1.aspmx.l.google.com.
danielcastelao.org.	900	IN	MX	80 aspmx.l.google.com.
danielcastelao.org.	900	IN	MX	110 aspmx2.googlemail.com.
danielcastelao.org.	900	IN	MX	140 aspmx5.googlemail.com.

;; Query time: 119 msec
;; SERVER: 127.0.0.53#53(127.0.0.53) (UDP)
;; WHEN: Mon Oct 21 20:04:16 CEST 2024
;; MSG SIZE  rcvd: 226
```

## 9. Rexistros AAAA de www.facebook.com
```bash
dig www.facebook.com AAAA

; <<>> DiG 9.18.28-0ubuntu0.22.04.1-Ubuntu <<>> www.facebook.com AAAA
;; global options: +cmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 41967
;; flags: qr rd ra; QUERY: 1, ANSWER: 1, AUTHORITY: 0, ADDITIONAL: 1

;; OPT PSEUDOSECTION:
; EDNS: version: 0, flags:; udp: 65494
;; QUESTION SECTION:
;www.facebook.com.		IN	AAAA

;; ANSWER SECTION:
www.facebook.com.	329	IN	CNAME	star-mini.c10r.facebook.com.

;; Query time: 14 msec
;; SERVER: 127.0.0.53#53(127.0.0.53) (UDP)
;; WHEN: Mon Oct 21 20:05:35 CEST 2024
;; MSG SIZE  rcvd: 74
```
