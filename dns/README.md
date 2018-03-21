# Практика. DNS

Аристархова Светлана КН-202

## Задания

#### 1. Изучить способы вызова программы nslookup.

Режим командной строки (вызов nslookup без параметров). Просмотреть справку – help.
Просмотреть и отметить установки параметров по умолчанию – set all. Выйти – exit.
Режим одного запроса (вызов nslookup с параметрами, список которых есть в справке).
Формат вызова – nslookup [опции] символьноеИмя серверИмён, например
nslookup –type=ns urfu.ru ns.urfu.ru

#### 2. Работая с nslookup в режиме одного запроса, выясните адреса серверов имён (NS) для:

```
>nslookup -type=ns urfu.ru
╤хЁтхЁ:  www.routerlogin.com
Address:  192.168.0.1

Не заслуживающий доверия ответ:
urfu.ru nameserver = ns1.urfu.ru
urfu.ru nameserver = ns2.urfu.ru
urfu.ru nameserver = ns3.urfu.ru

>nslookup -type=ns msu.ru
╤хЁтхЁ:  www.routerlogin.com
Address:  192.168.0.1

Не заслуживающий доверия ответ:
msu.ru  nameserver = ns3.nic.fr
msu.ru  nameserver = ns.msu.ru
msu.ru  nameserver = ns1.orc.ru
msu.ru  nameserver = ns.msu.net

выясните ip-адреса хостов для символьных имён

>nslookup urfu.ru
╤хЁтхЁ:  www.routerlogin.com
Address:  192.168.0.1

Не заслуживающий доверия ответ:
╚ь :     urfu.ru
Address:  212.193.82.20

>nslookup rbc.ru
╤хЁтхЁ:  www.routerlogin.com
Address:  192.168.0.1

Не заслуживающий доверия ответ:
╚ь :     rbc.ru
Addresses:  80.68.253.9
          185.72.229.9
```

#### 3. Перейти в режим командной строки nslookup. Выяснить имя и адрес dns-сервера, которому будут отправляться запросы

```
> root
╤хЁтхЁ яю єьюыўрэш■:  A.ROOT-SERVERS.NET
Address:  198.41.0.4
```

#### 4. Изучить команды перехода между серверами – server, lserver и root. Перейти на использование сервера с адресом 194.226.235.1 (команда server), затем – с адресом ns1.urfu.ru. Выяснить различие в функционировании server и lserver и использовать нужную команду для перехода от сервера 194.226.235.1 к серверу ns1.urfu.ru. Снова перейти к несуществующему серверу 194.226.235.1 и затем перейти к корневому серверу (команда root). Обратить внимание на то, что адрес корневого сервера известен, несмотря на то, что он задан символьным именем.

```
> server 194.226.235.1
╤хЁтхЁ яю єьюыўрэш■:  [194.226.235.1]
Address:  194.226.235.1

> server ns1.urfu.ru
DNS request timed out.
    timeout was 2 seconds.
DNS request timed out.
    timeout was 2 seconds.
DNS request timed out.
    timeout was 2 seconds.
DNS request timed out.
    timeout was 2 seconds.
*** Не найден адрес для сервера ns1.urfu.ru: Timed out
> lserver ns1.urfu.ru
*** Не найден адрес для сервера ns1.urfu.ru: No response from server

> server 194.226.235.1
DNS request timed out.
    timeout was 2 seconds.
╤хЁтхЁ яю єьюыўрэш■:  [194.226.235.1]
Address:  194.226.235.1

> lserver 194.226.235.1
╤хЁтхЁ яю єьюыўрэш■:  [194.226.235.1]
Address:  194.226.235.1

> root
╤хЁтхЁ яю єьюыўрэш■:  a.root-servers.net
Address:  198.41.0.4
```

#### 5. Перейти в режим запроса записей NS (set q=ns или set type=ns), выяснить адреса серверов имён для доменов верхнего уровня (и их общее количество):

```
>set type=ns

> com.
╤хЁтхЁ:  a.root-servers.net
Address:  198.41.0.4

com     nameserver = e.gtld-servers.net
com     nameserver = b.gtld-servers.net
com     nameserver = j.gtld-servers.net
com     nameserver = m.gtld-servers.net
com     nameserver = i.gtld-servers.net
com     nameserver = f.gtld-servers.net
com     nameserver = a.gtld-servers.net
com     nameserver = g.gtld-servers.net
com     nameserver = h.gtld-servers.net
com     nameserver = l.gtld-servers.net
com     nameserver = k.gtld-servers.net
com     nameserver = c.gtld-servers.net
com     nameserver = d.gtld-servers.net
e.gtld-servers.net      internet address = 192.12.94.30
e.gtld-servers.net      AAAA IPv6 address = 2001:502:1ca1::30
b.gtld-servers.net      internet address = 192.33.14.30
b.gtld-servers.net      AAAA IPv6 address = 2001:503:231d::2:30
j.gtld-servers.net      internet address = 192.48.79.30
j.gtld-servers.net      AAAA IPv6 address = 2001:502:7094::30
m.gtld-servers.net      internet address = 192.55.83.30
m.gtld-servers.net      AAAA IPv6 address = 2001:501:b1f9::30
i.gtld-servers.net      internet address = 192.43.172.30
i.gtld-servers.net      AAAA IPv6 address = 2001:503:39c1::30
f.gtld-servers.net      internet address = 192.35.51.30
f.gtld-servers.net      AAAA IPv6 address = 2001:503:d414::30

> org.
╤хЁтхЁ:  a.root-servers.net
Address:  198.41.0.4

org     nameserver = a0.org.afilias-nst.info
org     nameserver = a2.org.afilias-nst.info
org     nameserver = b0.org.afilias-nst.org
org     nameserver = b2.org.afilias-nst.org
org     nameserver = c0.org.afilias-nst.info
org     nameserver = d0.org.afilias-nst.org
a0.org.afilias-nst.info internet address = 199.19.56.1
a2.org.afilias-nst.info internet address = 199.249.112.1
b0.org.afilias-nst.org  internet address = 199.19.54.1
b2.org.afilias-nst.org  internet address = 199.249.120.1
c0.org.afilias-nst.info internet address = 199.19.53.1
d0.org.afilias-nst.org  internet address = 199.19.57.1
a0.org.afilias-nst.info AAAA IPv6 address = 2001:500:e::1
a2.org.afilias-nst.info AAAA IPv6 address = 2001:500:40::1
b0.org.afilias-nst.org  AAAA IPv6 address = 2001:500:c::1
b2.org.afilias-nst.org  AAAA IPv6 address = 2001:500:48::1
c0.org.afilias-nst.info AAAA IPv6 address = 2001:500:b::1
d0.org.afilias-nst.org  AAAA IPv6 address = 2001:500:f::1

> ru.
╤хЁтхЁ:  a.root-servers.net
Address:  198.41.0.4

ru      nameserver = a.dns.ripn.net
ru      nameserver = e.dns.ripn.net
ru      nameserver = f.dns.ripn.net
ru      nameserver = d.dns.ripn.net
ru      nameserver = b.dns.ripn.net
a.dns.ripn.net  internet address = 193.232.128.6
a.dns.ripn.net  AAAA IPv6 address = 2001:678:17:0:193:232:128:6
e.dns.ripn.net  internet address = 193.232.142.17
e.dns.ripn.net  AAAA IPv6 address = 2001:678:15:0:193:232:142:17
f.dns.ripn.net  internet address = 193.232.156.17
f.dns.ripn.net  AAAA IPv6 address = 2001:678:14:0:193:232:156:17
d.dns.ripn.net  internet address = 194.190.124.17
d.dns.ripn.net  AAAA IPv6 address = 2001:678:18:0:194:190:124:17
b.dns.ripn.net  internet address = 194.85.252.62
b.dns.ripn.net  AAAA IPv6 address = 2001:678:16:0:194:85:252:62
```

#### 6. Пройти по цепочке серверов имён от корня и, по необходимости меняя в запросе тип записей (set q=…), найти ip-адрес для символьного имени и записать промежуточные данные в виде цепочки результатов запросов.

cs.usu.edu.ru

```
> set type=ns
> ru.
╤хЁтхЁ:  www.routerlogin.com
Address:  192.168.0.1

Не заслуживающий доверия ответ:
ru      nameserver = e.dns.ripn.net
ru      nameserver = f.dns.ripn.net
ru      nameserver = a.dns.ripn.net
ru      nameserver = b.dns.ripn.net
ru      nameserver = d.dns.ripn.net

a.dns.ripn.net  internet address = 193.232.128.6
b.dns.ripn.net  internet address = 194.85.252.62
d.dns.ripn.net  internet address = 194.190.124.17
e.dns.ripn.net  internet address = 193.232.142.17
f.dns.ripn.net  internet address = 193.232.156.17
> lserver 193.232.128.6
╤хЁтхЁ яю єьюыўрэш■:  [193.232.128.6]
Address:  193.232.128.6

> edu.ru
╤хЁтхЁ:  [193.232.128.6]
Address:  193.232.128.6

EDU.RU  nameserver = ns.msu.RU
EDU.RU  nameserver = ns2.informika.RU
EDU.RU  nameserver = ns2.free.net
EDU.RU  nameserver = ns.informika.RU
EDU.RU  nameserver = ns.runnet.RU
ns.MSU.RU       internet address = 93.180.0.1
ns.RUNNET.RU    internet address = 194.85.32.18
ns.INFORMIKA.RU internet address = 194.226.215.65
ns2.INFORMIKA.RU        internet address = 194.190.241.65
> lserver 93.180.0.1
╤хЁтхЁ яю єьюыўрэш■:  [93.180.0.1]
Address:  93.180.0.1

> usu.edu.ru
╤хЁтхЁ:  [93.180.0.1]
Address:  93.180.0.1

usu.edu.ru      nameserver = ns.urgu.org
usu.edu.ru      nameserver = ns.usaaa.ru
> lserver ns.urgu.org
*** Не найден адрес для сервера ns.urgu.org: No response from server
> set type=A
> cs.usu.edu.ru
╤хЁтхЁ:  [93.180.0.1]
Address:  93.180.0.1

╚ь :     cs.usu.edu.ru
Served by:
- ns.usaaa.ru

          usu.edu.ru
- ns.urgu.org

          usu.edu.ru
```

www.imm.uran.ru

```
> set type=ns
> ru.
╤хЁтхЁ:  www.routerlogin.com
Address:  192.168.0.1

Не заслуживающий доверия ответ:
ru      nameserver = a.dns.ripn.net
ru      nameserver = b.dns.ripn.net
ru      nameserver = d.dns.ripn.net
ru      nameserver = e.dns.ripn.net
ru      nameserver = f.dns.ripn.net

a.dns.ripn.net  internet address = 193.232.128.6
b.dns.ripn.net  internet address = 194.85.252.62
d.dns.ripn.net  internet address = 194.190.124.17
e.dns.ripn.net  internet address = 193.232.142.17
f.dns.ripn.net  internet address = 193.232.156.17
> lserver 193.232.128.6
╤хЁтхЁ яю єьюыўрэш■:  [193.232.128.6]
Address:  193.232.128.6

> uran.ru
╤хЁтхЁ:  [193.232.128.6]
Address:  193.232.128.6

URAN.RU nameserver = ns2.uran.RU
URAN.RU nameserver = ns.uran.RU
ns.URAN.RU      internet address = 195.19.137.69
ns2.URAN.RU     internet address = 195.19.155.97
> lserver 195.19.137.69
╤хЁтхЁ яю єьюыўрэш■:  [195.19.137.69]
Address:  195.19.137.69

> set type=A
> www.imm.uran.ru.
╤хЁтхЁ:  [195.19.137.69]
Address:  195.19.137.69

╚ь :     www.imm.uran.ru
Address:  195.19.137.125
```

kma.imkn.urfu.ru

```
> set type=ns
> ru.
╤хЁтхЁ:  www.routerlogin.com
Address:  192.168.0.1

Не заслуживающий доверия ответ:
ru      nameserver = f.dns.ripn.net
ru      nameserver = a.dns.ripn.net
ru      nameserver = b.dns.ripn.net
ru      nameserver = d.dns.ripn.net
ru      nameserver = e.dns.ripn.net

a.dns.ripn.net  internet address = 193.232.128.6
b.dns.ripn.net  internet address = 194.85.252.62
d.dns.ripn.net  internet address = 194.190.124.17
e.dns.ripn.net  internet address = 193.232.142.17
f.dns.ripn.net  internet address = 193.232.156.17
> lserver 193.232.128.6
╤хЁтхЁ яю єьюыўрэш■:  [193.232.128.6]
Address:  193.232.128.6

> urfu.ru
╤хЁтхЁ:  [193.232.128.6]
Address:  193.232.128.6

URFU.RU nameserver = ns1.urfu.RU
URFU.RU nameserver = ns3.urfu.RU
URFU.RU nameserver = ns2.urfu.RU
ns1.URFU.RU     internet address = 212.193.66.21
ns2.URFU.RU     internet address = 212.193.82.21
ns3.URFU.RU     internet address = 212.193.72.21
> lserver 212.193.66.21
╤хЁтхЁ яю єьюыўрэш■:  [212.193.66.21]
Address:  212.193.66.21

> set type=A
> imkn.urfu.ru
╤хЁтхЁ:  [212.193.66.21]
Address:  212.193.66.21

╚ь :     imkn.urfu.ru
Address:  212.193.68.65
```

#### 7. Изучить способы получения с сервера всех записей (команда ls). Подключиться к нужному серверу, вывести на экран и сохранить в файл записи для:

edu.ru
```
> lserver 93.180.0.1
╤хЁтхЁ яю єьюыўрэш■:  [93.180.0.1]
Address:  93.180.0.1

> ls -d edu.ru > eduru.txt
[[93.180.0.1]]
####
Received 1800 records.
```

urfu.ru
```
> lserver 212.193.66.21
╤хЁтхЁ яю єьюыўрэш■:  [212.193.66.21]
Address:  212.193.66.21

> ls -t A urfu.ru > urfuru.txt
[[212.193.66.21]]
Received 0 records.
*** Can't list domain urfu.ru: Query refused
```

mail.ru
```
> lserver 217.69.139.112
╤хЁтхЁ яю єьюыўрэш■:  [217.69.139.112]
Address:  217.69.139.112

> ls -t MX mail.ru > mailru.txt
[[217.69.139.112]]
Received 0 records.
*** Can't list domain mail.ru: Query refused
```

#### 8. Получить «начальную запись зоны» (SOA – start of authority), выяснить вероятную дату последнего обновления зоны, время жизни записей в промежуточных кеширующих серверах и прочую информацию для:

```
> ns1.yandex.ru
╤хЁтхЁ:  google-public-dns-a.google.com
Address:  8.8.8.8

yandex.ru
        primary name server = ns1.yandex.ru
        responsible mail addr = sysadmin.yandex-team.ru
        serial  = 2018032194
        refresh = 600 (10 mins)
        retry   = 300 (5 mins)
        expire  = 2592000 (30 days)
        default TTL = 900 (15 mins)

> ns1.mail.ru
╤хЁтхЁ:  google-public-dns-a.google.com
Address:  8.8.8.8

mail.ru
        primary name server = ns1.mail.ru
        responsible mail addr = hostmaster.mail.ru
        serial  = 3312839537
        refresh = 900 (15 mins)
        retry   = 900 (15 mins)
        expire  = 604800 (7 days)
        default TTL = 60 (1 min)

> ns1.urfu.ru
╤хЁтхЁ:  google-public-dns-a.google.com
Address:  8.8.8.8

urfu.ru
        primary name server = ns1.urfu.ru
        responsible mail addr = hostmaster.urfu.ru
        serial  = 2012091861
        refresh = 3600 (1 hour)
        retry   = 1800 (30 mins)
        expire  = 2419200 (28 days)
        default TTL = 3600 (1 hour)
```

#### 9. Найти на www.iana.org (www.icann.org) полный список доменов верхнего уровня. Выяснить на www.nic.ru стоимость регистрации собственного домена в различных зонах, необходимые для этого документы и способы оплаты. Найти (например, в google) регистратора с минимальной стоимостью домена в зоне ru. Найти регистратора с минимальной стоимость домена в зонах com и org.

```
https://www.iana.org/domains/root/db - полный список доменов верхнего уровня.
https://www.nic.ru/catalog/domains/generic/ - стоимость регистрации собственного домена в различных зонах, необходимые для этого документы и способы оплаты.
https://domains.jino.ru/price/ - минимальной стоимостью домена в зоне ru.
https://ru.godaddy.com/ - минимальная стоимость домена в зонах com и org.
```