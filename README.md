# Activitat còpies de seguretat

## Presentació de l'activitat

### Introducció al cas

A la tasca anterior heu dissenyat una política de còpies de seguretat pel nostre nou client "Muntatges i Serveis Tècnics SL". Ara toca passar a l’acció i portar a la pràctica l’estudi anterior. El client demana que s’elaborin unes guies tècniques amb proves de concepte per tal que el seu personal estigui qualificat per implantar el pla de còpies de seguretat.

### Durada de l'activitat

La durada estimada de l'activitat és de 5 hores.

### Objectius de l'activitat

L’objectiu d’aquesta activitat és realitzar i documentar una política de còpies de seguretat tant pels equips client Windows, com pel servidor Linux.

### Competències treballades

a) Determinar la logística associada a les operacions d’instal·lació, configuració i manteniment de sistemes microinformàtics, interpretant-ne la documentació tècnica associada i organitzant els recursos necessaris.
c) Instal·lar i configurar programari bàsic i d’aplicació, assegurant-ne el funcionament en condicions de qualitat i seguretat.
j) Elaborar documentació tècnica i administrativa del sistema, complint les normes i reglamentació del sector, per al seu manteniment i l’assistència al client.

### Resultats d'aprenentatge i criteris d'avaluació

RA2. Gestiona dispositius d'emmagatzematge descrivint els procediments efectuats i aplicant tècniques per assegurar la integritat de la informació.

2.5 Selecciona estratègies per a la realització de còpies de seguretat.
2.6 Té en compte la freqüència i l'esquema de rotació.
2.7 Realitza còpies de seguretat amb diferents estratègies.

### Continguts

2.4 Còpies de seguretat i imatges de suport. Mitjans d'emmagatzematge.

### Capacitats clau

- Autonomia
- Organització del treball
- Responsabilitat
- Resolució de problemes

### Semàfor ús de la IA

🟠 Aquesta activitat permet un ús parcial o restringit.

- Permès per com a eina de suport en la millora de la redacció dels informes, cerca preliminar d'informació, estructuració d'idees o explicació de conceptes teòrics complexos.
- Condicions: Cal processar, entendre i validar sempre els resultats rebuts. **Està totalment prohibit copiar l'enunciat d'un exercici directament al xat de la IA i enganxar la resposta generada** per al lliurament final sense treball propi ni anàlisi crítica.

## Realització pràctica

### Part 1: Còpia seguretat dels equips clients Windows

Encara que en principi el DPR no contemplaria fer còpia dels arxius locals dels equips clients, se’ns demana fer una excepció amb l’equip Windows del director de l’empresa. En aquest equip es guarda informació important que no es vol tenir accessible al servidor de fitxers de l’empresa. Per aquest motiu és necessari definir una política de còpies de seguretat seguint l’esquema 3-2-1, es farà una còpia de seguretat a un disc secundari que té el propi equip i una segona còpia al cloud, en aquest cas, Google Drive usant l’eina **Duplicati**.

Com a prova de concepte per crear la guia, creareu una màquina virtual Windows 11 amb dos discos, en un instal·leu el sistema operatiu i un de secundari de 10 GB que servirà per emmagatzemar les còpies de seguretat. Per simular la part de Google Drive, **useu un compte que no sigui el d’escola** (podeu crear un compte específic per l’activitat).

Es desitja fer còpies de seguretat del perfil de l’usuari cada hora al disc secundari i a les 18:00 a Google Drive.

Documenteu el procediment de instal·lació de Duplicati, la configuració dels plans de còpies i observeu el funcionament. Per això, afegiu arxius a les carpetes de l’usuari, especialment a Documents. Podeu usar com a referència i ajuda el document [Guia còpies de seguretat amb Duplicati](Duplicati.md).

### Part 2: Còpia de seguretat del servidor Linux

Per fer les còpies del servidor Linux la solució proposada pel vostre responsable és Duplicity que permet fer còpies tant contra un mitjà local o un servidor remot. Combinat amb el programador de tasques (cron) es poden implementar les polítiques de còpia que es desitgin.

Has de crear una guia tècnica per explicar com es pot usar aquesta eina per fer còpies d’un servidor Linux.

Per fer aquesta guia i com a prova de concepte, usaràs una màquina virtual amb un Ubuntu Server instal·lat i li afegiràs un segon disc de 10 GB que simularà una unitat auxiliar.

#### Prova funcionament bàsic

Realitza els següents passos i documenta el procediment:

1. Inicialitza i formata en format xfs. Com simula una unitat externa, es muntarà manualment a /media/backup (primer cal crear la carpeta).
2. Instal·la duplicity.
3. Crea un parell d’usuaris més al sistema de manera que tinguin carpeta personal. Crea 4 arxius de 10 MB a la carpeta home del teu usuari.
4. Fes un còpia de seguretat de la carpeta /home.
5. Esborra els arxius i fes un restore per comprovar com es recuperen els arxius.
6. Afegeix un nou arxiu de 4 MB i fes una nova còpia. Observa com ara ha fet una còpia  incremental.
7. Desmunta la unitat de backup.

Ara passaràs a automatitzar el procés de les còpies utilitzant uns scripts bàsics i el programador de tasques (cron). Un aspecte molt important a nivell de seguretat, és que la unitat de backup ha d’estar per defecte, desmuntada. De manera que el primer pas sempre serà muntar la unitat i el darrer desmuntar-la, un cop s’ha fet la còpia.

#### Script còpia completa

1. Crea un script anomenat `fullbackup.sh` que realitzi la còpia completa de la carpeta /home i l’emmagatzemi al volum muntat. Usa la variable d’entorn PASSPHRASE (per donar valor a una variable d’entorn cal afegir a l’script una línia amb export PASSPHRASE=contrasenya) per no haver d’escriure la passphrase en el moment de l’execució. Recorda de donar permisos d’execució a l’script.
2. Programa el cron com a root per tal que s’executi l’script cada diumenge a les 23:00 hores.

#### Script còpia incremental

1. Crea un segon script anomenat `incrbackup.sh` que realitzi la còpia incremental de la carpeta /home i l’emmagatzemi al volum muntat. Usa la variable d’entorn PASSPHRASE (per donar valor a una variable d’entorn cal afegir a l’script una línia amb export PASSPHRASE=contrasenya) per no haver d’escriure la passphrase en el moment de l’execució. Recorda de donar permisos d’execució a l’script.
2. Programa el cron com a root per tal que s’executi l’script de còpia incremental de dilluns a dissabte a les 23:00 hores.

## Materials i enllaços de suport

- [Duplicati](https://www.duplicati.com/)
- [Duplicity](https://duplicity.gitlab.io)
- [Duplicty man pages](http://manpages.ubuntu.com/manpages/trusty/man1/duplicity.1.html)
- [WaytoIT. Creando archivos de prueba con fsutil](https://waytoit.wordpress.com/2015/03/15/creando-archivos-con-fsutil/)
- [WaytoIT. Creando archivos de prueba en Linux](https://waytoit.wordpress.com/2015/03/21/creando-archivos-de-prueba-en-linux/)
- [Progamant tasques amb cron](https://geekytheory.com/programar-tareas-en-linux-usando-crontab)
