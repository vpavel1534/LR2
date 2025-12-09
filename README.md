# LR2

# Лабораторная работа №2
Выполнил: Воробьев Павел
--- 

## Разбор методик эксплуатации уязвимостей  
Дисциплина: «Защита программного обеспечения защищенных автоматизированных систем»

---

## Цель работы

1. Ознакомиться с современными уязвимостями класса RCE (Remote Code Execution) и LPE (Local Privilege Escalation).  
2. Изучить примеры практических PoC-эксплойтов из открытых источников.  
3. Проанализировать основные шаги, которые выполняет эксплойт при атаке.  
4. Сформировать перечень уязвимостей с указанием источников и кратким описанием.  

---

## 1. Перечень рассмотренных уязвимостей

### 1.1. Уязвимости класса RCE
CVE-2021-44228 (Log4Shell) – Apache Log4j2 Remote Code Execution
Критическая уязвимость в библиотеке Apache Log4j2, позволяющая неаутентифицированному атакующему выполнить произвольный код через JNDI lookup при обработке логируемых данных.
PoC: https://github.com/trickest/log4shell

CVE-2023-38831 – WinRAR Remote Code Execution
Уязвимость в алгоритме обработки архивов WinRAR, позволяющая злоумышленнику сконструировать архив, при открытии которого (в частности, при просмотре файла внутри) выполнится произвольный код.
PoC: https://github.com/b1tg/CVE-2023-38831-winrar-exploit

CVE-2023-22515 – Atlassian Confluence Data Center/Server Privilege Escalation / Broken Access Control
Критическая уязвимость контроля доступа (унаследованная категория от CVE-2023-22518) в Confluence, позволяющая неаутентифицированному атакующему создать административную учётную запись и получить полный контроль над экземпляром.
PoC: https://github.com/Chocapikk/CVE-2023-22515

CVE-2023-38545 – libcURL SOCKS5 Heap Buffer Overflow (High Severity)
Уязвимость переполнения кучи в библиотеке libcURL, которая может привести к выполнению произвольного кода или сбою принудительного завершения работы, когда cURL настроен на использование прокси SOCKS5 с узким буфером хоста.
PoC: https://github.com/testanull/CVE-2023-38545

CVE-2023-3519 – Citrix NetScaler ADC/Gateway Unauthenticated Remote Code Execution
Критическая уязвимость в Citrix NetScaler ADC и Gateway, позволяющая неаутентифицированному удалённому злоумышленнику выполнить произвольный код на устройствах, сконфигурированных в качестве шлюза (Gateway).
PoC: https://github.com/Chocapikk/CVE-2023-3519
### 1.2. Уязвимости класса LPE
CVE-2021-4034 (PwnKit) – Polkit pkexec Local Privilege Escalation
Критическая уязвимость в утилите pkexec (часть Polkit), существовавшая более 12 лет. Позволяет непривилегированному локальному пользователю получить полные права root за счёт обработки аргументов командной строки и манипуляции с переменными окружения.
PoC: https://github.com/arthepsy/CVE-2021-4034

CVE-2022-2588 – Linux Kernel nftables Use-After-Free LPE
Уязвимость use-after-free в подсистеме nftables ядра Linux, позволяющая локальному пользователю повысить свои привилегии до root (kernel panic также возможен). Эксплуатация связана с работой с наборами объектов nft_set.
PoC: https://github.com/Markakd/CVE-2022-2588

CVE-2023-32629 (GameOver(lay)) – Linux Kernel OverlayFS Local Privilege Escalation
Уязвимость в подсистеме OverlayFS ядер Linux (с версии 5.14). Позволяет локальному пользователю повысить привилегии до root, используя особенность обработки атрибутов файлов (в частности, trusted.overlayfs.*) в определённых конфигурациях.
PoC: https://github.com/sxlmnwb/CVE-2023-32629

CVE-2022-34918 – Linux Kernel nftables Stack Overflow LPE
Уязвимость переполнения стека (stack overflow) в подсистеме nftables ядра Linux. Локальный пользователь может создать специальные правила nftables, приводящие к переполнению и потенциальному выполнению кода в пространстве ядра с правами root.
PoC: https://github.com/H4K6/CVE-2022-34918-LPE-PoC

CVE-2021-1732 – Windows Win32k Elevation of Privilege Vulnerability
Уязвимость в драйвере win32k.sys операционной системы Windows. Позволяет локальному атакующему повысить свои привилегии от уровня пользователя до уровня SYSTEM (NT AUTHORITY\SYSTEM) за счёт некорректной обработки объектов окна (window objects).
PoC: https://github.com/exploitblizzard/Windows-Privilege-Escalation-CVE-2021-1732
## 2. Разбор отдельных PoC-эксплойтов

Ниже приведён краткий анализ четырёх выбранных PoC: двух для RCE и двух для LPE.

## 3. Выводы
