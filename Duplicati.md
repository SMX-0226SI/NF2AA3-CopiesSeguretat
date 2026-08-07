# Guia còpies de seguretat amb Duplicati

## Instal·lació i preparació Duplicati

1. Amb la màquina virtual apagada, afegim un segon disc de 10 GB.
2. Engega la màquina virtual i inicia sessió a Windows 11. A l'adminisrtrador de discs, inicialitza i formata el nou disc com a NTFS.
3. Descarrega: Ves a la web oficial de Duplicati i baixa l'instal·lador per a Windows (.msi).
4. Instal·la: Executa l'arxiu i segueix l'assistent. Assegura't de marcar l'opció per executar-lo a l'inici (Launch Duplicati at startup).
5. Obre la interfície: Duplicati funciona a través del navegador web. Un cop instal·lat, s'obrirà automàticament a http://localhost:8200.

## Configuració de la còpia local (unitat externa)

**Objectiu**: fer còpies incrementals dels perfils d'usuari cada hora.

1. Fes clic a "Afegir còpia de seguretat" > "Configurar una nova còpia de seguretat".
2. Pas 1: General:
   - Nom: Còpia Local - C Users
   - Xifratge: Deixa AES-256.
   - Contrasenya: Genera una contrasenya forta.

> MOLT IMPORTANT: Desa aquesta contrasenya en un gestor de contrasenyes o en paper. Sense ella, no podràs recuperar les dades.

3. Pas 2: Destí
   - Tipus d'emmagatzematge: Unitat o carpeta local.
   - Ruta de la carpeta: Navega i selecciona el segon disc que has afegit (per exemple, D:\Backups\DuplicatiLocal).
4. Pas 3: Dades d'origen
   - Navega per l'arbre de carpetes i marca la casella de: C:\Users.
   - Recomanació: Dins de "Filtres" o "Excloure", et suggereixo afegir una regla per excloure arxius temporals (com la carpeta AppData\Local\Temp o les memòries cau dels navegadors), ja que ocupen molt espai i canvien constantment.
5. Pas 4: Horari
    - Marca "Executar còpies de seguretat automàtiques".
    - Pròxima vegada: Deixa l'hora actual.
    - Repetir cada: 1 hora.
    - Dies permesos: Marca tots els dies.
6. Pas 5: Opcions
    - Mida del volum: 50MB (per defecte està bé).
    - Retenció de còpies: Selecciona "Retenció intel·ligent de còpies de seguretat" (guarda una cada hora les últimes 24h, una diària la setmana següent, etc., per estalviar espai).
    - Desa la configuració.

