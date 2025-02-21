---
title: "DNS FWD на MikroTik"
description: "Маршрутизация по списку доменов"
date: "2025-02-21"
draft: false
tags:
  - dns
  - mikrotik
---

---

## Введение

С каждым годом количество устройств, подключенных к интернету, растет с невероятной скоростью. Это приводит к исчерпанию адресного пространства IPv4, которое использовалось на протяжении десятилетий. В ответ на эту проблему была разработана новая версия протокола — IPv6. В этой статье мы рассмотрим, что такое IPv6, его преимущества и вызовы, с которыми он сталкивается.

## Что такое FWD Запись?

FWD запись позволяет перенаправитиь DNS-запросы для выбранного домена на сервер отличный от основного через Forwarder
Forwarder в свою очередь это сущность внутри маршрутизатора которая перенаправляет запросы к выбраному классическому DNS или DNS over HTTPS серверу
```
/ip dns static
forwarders add doh-servers=https://cloudflare-dns.com/dns-query name=cf.dns verify-doh-cert=no
add comment="DNS for FWD" forward-to=cf.dns name=router.dns type=FWD

add address-list=Censored comment=TOR forward-to=router.dns match-subdomain=yes name=\
    torproject.org type=FWD
```


