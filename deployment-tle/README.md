# Installatie & Deployment Laravel

Om je project op een onlineomgeving te krijgen ga je werken met een VPS. Als team heb
je deze aangevraagd via school, maar je kunt ook een eigen serveromgeving gebruiken.

Deze handleiding werkt met Ubuntu (v22.04 of v24.04) om de noodzakelijke tools te installeren,
en te zorgen dat je een werkende webserver hebt waar je Laravel project kan draaien.

### Let op voor je aan de slag gaat!

> - Je moet voor de stappen hieronder je logingegevens paraat hebben van de aanvraag voor de VM
> - Als je gegevens (zoals je wachtwoord) wilt kopiëren en plakken op Windows in Powershell moet je jouw rechtermuisknop gebruiken om te plakken
> - Als er gevraagd wordt om een fingerprint toe te voegen moet je met "yes" antwoorden (dit wordt 2 keer gevraagd in het proces)
> - Als er geen feedback komt vanuit de gedraaide commands is dat een goed teken. Als er wel feedback is, dan is dit vaak een foutmelding.
> - Als je grote fouten krijgt, roep dan Antwan erbij

## Installatie

Download de zip en pak deze uit in een voor jou logische map. Open je Terminal (mac) of Powershell
(Windows) en navigeer naar de map waar je de bestanden hebt gedownload. Als je in de goede map staat
kun je de bestanden verkregen via docent uploaden naar jullie server. Draai het volgende commando en
vervang `<user>` en `<ip>` met je eigen gegevens (`<>` tekens moeten hier niet meer staan na het aanpassen
naar je eigen gegevens):

```bash
scp .env.example nginx.conf install_tools.sh configure_webserver.sh deploy.sh <user>@<ip>:/home/<user>/
```

Log nu in op de server via:

```bash
ssh <user>@<ip>
```

> Vanaf nu ben je ingelogd op de server en voer je de commando's dus uit op de server. En niet meer op je eigen laptop.

Valideer dat het uploaden van de bestanden goed is gegaan door het volgende commando te draaien:

```bash
ls -al
```

Je zou nu de scripts moeten zien die je eerder op je eigen laptop hebt uitgepakt. Klopt dit? Dan kun je verder.
Om de scripts te kunnen draaien moet je ze qua rechten aanpassen zodat ze 'executable' zijn:

```bash
chmod u+x install_tools.sh configure_webserver.sh deploy.sh
```

Run nu het eerste script als volgt:

```bash
./install_tools.sh
 ```

Hiermee worden alle noodzakelijke tools geïnstalleerd op de server. Het commando`sudo` geeft je
meer rechten dan een gewone gebruiker, maar zoals bekend 'with great powers, comes great responsibility'.
Daarom moet je 1 keer opnieuw je wachtwoord invullen om te controleren of je echt zelf nog achter de
computer zit. Na voltooiing heb je het volgende geïnstalleerd:

- Een aantal basispakketten voor webcommunicatie
- Git
- Nginx (webserver)
- PHP 8.3 inclusief noodzakelijke extensions
- Composer
- NVM (met Node LTS & NPM)
- SSH key

> Test of je installatie goed is gegaan door naar http://\<jouwip> te gaan in de browser. Als
> je nu een nginx startpagina ziet, is het goed gegaan en kun je door naar de volgende stap.

## Configuratie webserver

In plaats van de default nginx startpagina wil je uiteraard je eigen github project hier zien.

Hiervoor moet je de SSH key van de server toevoegen aan jouw Github project deployment keys,
zodat de server namens jou op Github kan inloggen

- Draai `cat ~/.ssh/id_rsa.pub` op de server om jouw key te kunnen zien
- Kopieer deze key (dus de hele output van het commando)
- Ga naar github.com en open jouw repository
    - Ga naar **Settings** en daarbinnen naar **Deploy keys**
    - Voeg een nieuwe toe en plak hier jouw gekopieerde key
    - Geef als titel "hr-vm-tle1"
    - Laat het vinkje voor write access uitstaan

Run nu het volgende script. Let op, dit doe je **ZONDER** sudo (vul je wachtwoord in voor `sudo` wanneer
hier tussendoor om wordt gevraagd). Je krijgt 3 vragen waarvan de uitleg onder het commando staat:

```bash
./configure_webserver.sh
```

- Vraag 1: Vul hier je SSH (!!) github link in (ziet eruit als `git@github.com:<username>/<repo>.git`)
- Vraag 2: De naam van je project ZONDER spaties of hoofdletters (bv: laravel-chess of open-hiring)
- Vraag 3: De naam die in de titel van je website komt te staan (bv: Laravel Chess of Open Hiring)

> Na het draaien van dit script kun je opnieuw naar http://\<jouwip> gaan in de browser. Je zou hier
> nu je Laravel project werkend moeten zien draaien! 🚀

## Deployen nieuwe versie

Wanneer je een nieuwe release wilt (lees: de nieuwe versie uit de main branch) doen op de server, kun je
dit doen door in te loggen via SSH en in je homefolder `./deploy.sh` te draaien. De nieuwe versie van
je project zou nu zichtbaar moeten zijn op http://\<jouwip>

> Heb je meer nodig in je deployment flow kun je het deploy script natuurlijk aanpassen.
> Denk hierbij aan extra artisan commando's omdat je bijvoorbeeld een db:seed wilt doen.
> Je kunt dit natuurlijk ook handmatig in de `/var/www/production` folder doen (Denk aan
> aanpassing van je .env bestand), let hier dan wel op de rechten van de folder. Mocht dit
> misgaan kun je altijd `sudo -u www-data` voor je commando neerzetten. (Bijvoorbeeld:
> `sudo -u www-data php artisan db:seed`)

## NIET DOEN: Domein met SSL Certificaat

De website draait nu op `http://\<jouwip>` en is door iedereen (binnen Nederland i.v.m. beveiliging in
de Hogeschool firewall) te bezoeken. De stap om ook echt een domeinnaam (hr.nl, mijn-website.nl, etc.)
toe te voegen slaan we voor nu over.

> **DIT DOEN WE OM DE KLANT TE BESCHERMEN EN GEEN WILDGROEI AAN DOMEINEN
> TE KRIJGEN DIE HELEMAAL NIET VAN EEN ECHTE OPDRACHTGEVER ZIJN**

Mocht je hier voor een privéproject zelf in willen duiken kun je de onderste toegevoegde bron gebruiken.

## Bronnen

- https://laravel.com/docs/11.x/deployment#nginx
- https://www.digitalocean.com/community/tutorials/how-to-install-linux-nginx-mysql-php-lemp-stack-on-ubuntu
- https://computingforgeeks.com/how-to-install-php-8-3-on-ubuntu/
- https://www.digitalocean.com/community/tutorials/how-to-secure-nginx-with-let-s-encrypt-on-ubuntu-22-04
