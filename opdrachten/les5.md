# Les 5

Bij deze les kan je naast de documentatie van Laravel.com ook gebruik maken van 
[https://laracasts.com/series/30-days-to-learn-laravel-11](https://laracasts.com/series/30-days-to-learn-laravel-11) aflevering 7, 8, 9



## Opdracht - Migration

1. [Creëer de migration](https://laravel.com/docs/11.x/migrations#generating-migrations) zodat de bijbehorende databasetabel wordt aangemaakt. 
2. Open het aangemaakte migration bestand (in de map `database` van je project) en [voeg de velden toe](https://laravel.com/docs/11.x/migrations#creating-tables) die je nodig hebt.
3. Voer de migration uit in de terminal
   ```
   php artisan migrate
   ```
   Met de volgende regel kan je zien of er nog migrations zijn die niet uitgevoerd zijn
 
   ```
   php artisan migrate:status
   ```
 4. Vul de database met (dummy) data. Dit kan je doen door de [database te koppelen aan PHPStorm](https://www.jetbrains.com/help/phpstorm/mariadb.html) en daar de databasetabel te openen. Let op dat de datasource `sqlite` is.
   <img src="../images/phpstorm-database.png" width="40%"/>
   
   [Een nieuwe rij toevoegen](https://www.jetbrains.com/help/phpstorm/table-editor.html) doe je als volgt:
   
   - Dubbelklik op de naam van de tabel om deze te openen
   - Druk op het + teken (Add Row) bovenin de balk. (Een nieuwe rij wordt toegevoegd aan de tabel)
   - Vul de benodigde informatie in (behalve de primairy key)
   - Druk op CTRL + ENTER (CMD + ENTER voor Mac) om de data definitief toe te voegen.

## Opdracht - Model

Deze opdracht kan je meteen toepassen in je eigen project of je kunt verder gaan in het basic project waar je vorige week mee begonnen was. In deze opdracht maak je een model. De inhoud van het model zal uiteindelijk getoond worden in de View.

1. **Maak** een model aan voor een item dat je wilt gaan opslaan in de database. Bijvoorbeeld een Product, Movie, Reservation. Kies niet voor User, dit Model bestaat al. Voor het aanmaken van het model kan je gebruik maken van een [Artisan commando](https://laravel.com/docs/11.x/eloquent#generating-model-classes). Je kunt zelfs meteen de migration en controller creëren.
2. Open je Model. Bovenaan in je code zie je ongeveer de volgende regel staan:
   ```PHP
   <?php
   namespace App\Models;
   ```
   **Onderzoek** wat namespaces zijn en waarvoor ze dienen. 
4. Open de bijbehorende controller (bijv ProductController) en ga naar de index functie. 
5. Maak hier een nieuwe instance van het model aan en geef het model mee aan de View. 
   ```PHP
   $product = new Product();
   $product->title = 'Phone';
   $product->price = 1050;
   ```
6. **Toon** de onderdelen van het model in de View.

## Opdracht - Get data and show models

1. Haal het eerste item uit de database op, op basis van het id met de [`find()`](https://laravel.com/docs/11.x/eloquent#retrieving-single-models) functie in de `show()` functie van de `Controller`
2. Stuur het model mee aan de `View`.
3. Toon de data van het opgehaalde model in de `View`

**Meerdere items tonen**

4. Haal [alle](https://laravel.com/docs/11.x/eloquent#retrieving-models) items op in de `index()` functie van de `Controller`.
5. Geef de models mee aan de `View`.
6. Gebruik een loop om alle models te tonen in de `View`.

## Opdracht - Take the next step

Ga verder met het bewerken, verwijderen van de Models. Je kunt ook Models aanmaken en met daarbij ook direct de **Resource Controller**, **Migration** en de **Seeder**. Wil je weten welke mogelijkheden er zijn dan kan je voor elk artisan commando het woordje `help` schrijven. Bijvoorbeeld
```bash
php artisan help make:model
```

Wees gerust, je kunt niks stuk maken. Je kunt dus helemaal los gaan 🤪. Zeker als je regelmatig commit in GIT, heb je altijd een mogelijkheid om naar een vorige versie terug te gaan of door in je project een **Rollback** te doen. Je kunt dit zelf proberen. 
- Commit (en push) eerst de wijzigingen tot nu toe.
- Maak een wijziging in je project. Maak bijvoorbeeld een `View` aan en vul deze met een standaard HTML-pagina.
- Ga in PHPStorm naar `Git > Uncommitted Changes > Rollback...`

Je kunt nu kiezen welke bestanden je wilt _terugdraaien_ naar de versie van je laatste Commit. Tijdens een Commit kan je ook nog kiezen om per bestand een Rollback te doen, door met de rechtermuis op het bestand te klikken. 
