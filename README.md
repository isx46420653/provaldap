# ldapserver19:base

## ASIX M06-ASO Pau Martín @edt Curs 2019-2020

### Examen 08 - 11 - 2019

1. Definim la base de dades al fitxer slapd.conf, diem qui és l'usuari administrador i definim les ACL.

2. Modifiquem el fitxer ldap.conf i afegim la base del nostre servidor. *BASE dc=pau,dc=cat*

3. A continuació he creat els esquemes, el de indepeOrgPerson que serà un objecte fill de inetOrgPerson, i també el marchenaAccount que serà un auxiliar objecte fill de TOP.

4. Un cop creats els dos esquemes i afegits als include del fitxer slapd.conf, crearem l'estructura de dades amb les entitats a afegir, 1 organizationalUnit anomenada socis i 3 entitats dins d'aquesta, totes elles seràn indepeOrgPerson.

5. Aleshores crearem el fitxer de modificació per als socis que també seràn marchenaAccount.

6. Modifiquem el contingut del fitxer install.sh per a crear l'estructura del servidor mitjançant el fitxer **pau.cat.ldif**.

7. Crearem la imatge mitjançant el DockerFile i arrancarem el servidor comprovant que tot funciona correctament: `docker build -t prova .`

8. Hi entrem per a configurar-lo manualment i poder veure els errors: `docker run --rm --name ldapserver -h ldapserver -it prova /bin/bash`
