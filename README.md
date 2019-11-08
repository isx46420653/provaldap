# provaldap:2019

# github: isx46420653/provaldap

# dockerhub: isx46420653/provaldap

## ASIX M06-ASO Pau Martín @edt Curs 2019-2020

## Examen 08 - 11 - 2019

### Base 'dc=pau,dc=cat'

1. Definim la base de dades al fitxer slapd.conf, diem qui és l'usuari administrador i definim les ACL.

2. Modifiquem el fitxer ldap.conf i afegim la base del nostre servidor. *BASE dc=pau,dc=cat*

3. A continuació creem els esquemes, el de indepeOrgPerson serà un objecte fill de inetOrgPerson, i el marchenaAccount serà un objecte auxiliar fill de TOP.

4. Un cop creats els dos esquemes els afegim als include del fitxer slapd.conf, després, crearem l'estructura de dades amb les entitats a afegir, 1 organizationalUnit anomenada socis i 3 entitats dins d'aquesta, totes elles seràn indepeOrgPerson.

5. Aleshores crearem el fitxer de modificació per als socis que també seràn marchenaAccount.

6. Modifiquem el contingut del fitxer install.sh per a crear l'estructura del servidor mitjançant el fitxer **pau.cat.ldif**.

7. Crearem la imatge mitjançant el fitxer DockerFile: `docker build -t prova .`

8. Arranquem el contenidor i hi entrem per a configurar manualment el servidor i poder veure si hi han errors: `docker run --rm --name ldapserver -h ldapserver -it prova /bin/bash`

9. Instal·lem el servidor i provem que tot funciona, quan sigui aixi ho tornarem a fer però ara des de fora del contenidor, sortim, i tornem a arrancar un contenidor, però ara l'executarem en mode detach: `docker run --rm --name ldapserver -h ldapserver -d prova`.

Executarem els canvis amb ldapmodify: `ldapmodify -x -h 172.17.0.2 -D 'cn=Manager,dc=pau,dc=cat' -w secret -f marchena.ldif`

Comprovem que tot ha funcionat: `ldapsearch -x -LLL -h 172.17.0.2 -b 'dc=pau,dc=cat' -D 'cn=Manager,dc=pau,dc=cat' -w secret`

10. Un cop sabem que tot funciona correctament, creem una imatge actualitzada i l'anomenem **isx46420653/provaldap:2019**, també en creem una igual amb el nom **isx46420653/provaldap:latest**. I les pujem a [DockerHub](https://hub.docker.com/repository/docker/isx46420653/provaldap) amb `docker push`.

11. Els fitxers de configuració de la imatge i del servidor estan guardats al repositori de [Github](https://github.com/isx46420653/provaldap).
