# Les 3

## Nieuw project aanmaken met versiebeheer

Bij een professionele werkwijze hoort versiebeheer. Bij versiebeheer staan al je bestanden in een 'repository' waarin je versies van je project 'commit'. Deze commits zijn snapshots van je project waardoor je kunt zien wat er op welk moment aangepast is, en waardoor je aanpassingen ook weer terug kunt draaien. Wij gebruiken hiervoor het versiebeheerprogramma 'git'.

Als backup van je code, en om samen te kunnen werken of code te delen, is het verstandig ook een kopie van je repository online te zetten. Hiervoor gebruiken we het online platform 'GitHub'.

Hieronder staat een stappenplan voor het aanmaken van een nieuwe project met lokaal versiebeheer en een online koppeling.

We beginnen met het aanmaken van een nieuw Laravel project:

* Maak een map aan voor je Laravel project
* Ga in de terminal (Powershell) naar deze map
* Check met `pwd` of je in de juiste map staat
* Creëer het nieuwe project: `composer create-project laravel/laravel .` (vergeet de punt niet, die betekent dat je het project in de huidige directory wilt zetten)

Open nu je project in PHPStorm. Er komen popups met vragen om npm te draaien en om helpercode te genereren die je kunt toestaan.

De prettigste manier om Laravel te ontwikkelen is door drie terminal vensters te openen in PHPStorm: één om de webserver te draaien, één voor npm en één waar je zelf dingen in kunt doen zonder dat je steeds de server hoeft te stoppen en starten. Open de drie terminal vensters:
1. `php artisan serve`
2. `npm run dev`
3. Hier run je nog niks in

De derde terminal gebruiken we nu om een git repository met branch 'main' aan te maken:
* `git config --global init.defaultBranch main` (dit hoeft alleen de eerste keer)
* `git init`

Je ziet nu in PHPStorm een tabje erbij komen (links boven) voor je versiebeheer. 
* Selecteer in dit tabje alle bestanden, en commit ze met de omschrijving 'Initial Commit'

Je hebt nu lokaal versiebeheer voor je project geïnstalleerd waarin je je project op professionele wijze kunt ontwikkelen. De volgende stap is om je lokale versiebeheer te koppelen met een online repository.
* Ga naar [Github](https://github.com)
* Maak daar een een volledig lege repository aan (geen readme, geen gitignore, geen license)
* In PHPStorm kies je nu in het menu voor: Git - Push
* Klik op 'define remote' en in de popup die je krijgt plak je de URL van je repository (name: origin is al goed ingevuld)
* Als je nu je code 'pusht' krijg je (de eerste keer) de vraag om Jetbrains toegang te geven via 'Login via Github'
* Doorloop het login proces en geef toegang

Je project is nu klaar voor de start :-)

## Breeze toevoegen

Composer is een tool waarmee je code kunt downloaden. We hebben dit al gebruikt om het volledige Laravel project te creëren, en gaan het nu weer gebruiken om een inlogsysteem (Breeze) toe te voegen aan onze site.

Ga hiervoor weer naar je derde tabblad, en installeer Breeze:
* `composer require laravel/breeze --dev`
* `php artisan breeze:install`

Bekijk je site om te zien wat er veranderd is.

## Routes en Controllers

Oefen met de opdrachten rond [Routes en Controllers](./route.md).

## Opdracht - User Stories

- Beschrijf de werking en de functionaliteit van je applicatie. 
  - Denk in User Stories, taken en stakeholders.
- Stel de prioriteit vast met de MoSCoW methode. 
  - Maak het jezelf niet te moeilijk en begin met makkelijke taken. Begin niet met de login, maar volg de praktijkonderdelen uit de lessen. Vertaal bijvoorbeeld eerst [opdracht 1](https://github.com/HR-CMGT/PRG05-2023-2024/blob/main/opdrachten/les3.md#opdracht-1---basisproject-laravel) naar jouw eigen systeem.
  - Gebruik ter referentie toelichting_praktijkopdracht.pdf
- Maak hiervan een planning voor de komende weken.

## Opdracht - ERD

Doorloop de user stories van je project en bepaal aan de hand van deze taken welke informatie je wilt gaan opslaan in de database. 
Maak een ERD in bijvoorbeeld [Miro](https://miro.com/nl/), [Lucidchart](https://www.lucidchart.com/pages/landing) of [draw.io](https://www.drawio.com/)

Hou rekening met de volgende onderdelen: 
1. Zorg dat je data maar op 1 plek wordt opgeslagen. Dus bijvoorbeeld de adresgegevens van een klant maar in 1 tabel.
2. Wanneer er sprake is van een 1-op-veel relatie, let dan goed op de primairy en foreign keys.
3. Wanneer er sprak is van een veel-op-veel relatie dat je een koppeltabel moet maken. 
4. Gebruik Engelse naamgeving.
5. Naam van de tabel heeft kleine letters en is in meervoud.
6. Wanneer een veld meerdere woorden bevat zijn de woorden gescheiden voor een underscore (`remember_token`).

## Opdracht - Changelog

- Maak in de map `Praktijkopdracht` een bestand `readme.md`, of
- *Alternatief:* maak een map `_changelog` in je Laravel project, en zet daarin de `readme.md` om de changelog binnen je project te houden.
- Hierin maak je een changelog aan met de meeste recente datum bovenaan.
- **Voor aanvang van les 4** noteer je in je changelog de User Stories en een afbeelding van je ERD. 
  - Upload de afbeelding naar een map `images` die je aanmaakt in de map van je changelog.
  - In MarkDown voeg je een plaatje toe met de volgende code:
    ```
    ![naam van de afbeelding](pad-naar-afbeelding)
    ``` 
