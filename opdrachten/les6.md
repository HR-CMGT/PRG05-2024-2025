# Les 6

Bij deze les kan je naast de documentatie van Laravel.com ook gebruik maken van 
https://laracasts.com/series/30-days-to-learn-laravel-11 aflevering 11

In deze les gaan we aan de slag met relaties die tussen Modellen kunnen bestaan. Bijvoorbeeld:

- 1-op-veel
    - `Product` heeft meerdere `Reviews`
    - `Review` hoort bij één `Product`
- Veel-op-veel
    - `Product` heeft meerdere `Categories`
    - `Category` hoort bij meerdere `Products`

Vorig jaar hebben we gezien dat bij een 1-op-veel relatie het nodig was om een **foreign key** toe te voegen aan de tabel.
Voor de veel-op-veel relatie hebben we een andere oplossing nodig en dat is een **pivot table** (**koppeltabel**).
Bij het aanmaken van de database moeten we hier dus rekening mee houden.

Om hiermee te oefenen kun je in je eindproject een nieuw `Model` aanmaken dat een relatie zal hebben met een bestaand Model. 
Kies een Model dat past bij jouw context. Hieronder een **voorbeeld** van een stappenplan.

## Opdracht - Maken `Review` Model

1. Maak `Review` Model aan met behulp van het
   [Artisan commando](https://laravel.com/docs/11.x/eloquent#generating-model-classes). Maak ook meteen de
   **Migrations** en **Controller** aan (dit kan een gewone Controller of een Resource Controller zijn, afhankelijk van de context).
2. Vul de Migration en **Voeg** de benodigde velden toe aan de `Migrations` die je nodig hebt en voeg de **foreign keys** 
   toe voor de 1-op-veel relatie. Dit doe je door een 
   veld toe te voegen met `foreignId()`. Zie [Laravel documentatie](https://laravel.com/docs/11.x/migrations#column-method-foreignId)
3. Koppel de `Review` aan de `Product` in het `Model`. Kies hiervoor de juiste relatie in de 
   [Laravel documentatie](https://laravel.com/docs/11.x/eloquent-relationships).
5. Maak je een foutje met een `Migration`. Je kunt altijd een stap terug met het volgende commando. Let op je moet
   de `down` functie in de migration goed hebben gedefinieerd.
   ```
   php artisan migrate:rollback
   ```
   Je kunt ook een aanpassing maken aan een migration en de database opnieuw laten opbouwen. Let op hiermee verwijder
   je alle data in de database.
   ```
   php artisan migrate:fresh
   ```

## Opdracht - Voeg reviews toe aan Product

Kies welke CRUD-functionaliteit je nodig hebt voor het nieuwe Model. Bij een `Review` is het bijvoorbeeld handig om 
alleen de `store` functie te maken, omdat het create formulier op de `product.show` pagina staat. 

Werk de benodige CRUD-functionaliteit uit.
1. Zorg ervoor dat je in de `products.show` pagina de reviews van het product toont.
2. Maak een formulier aan om een review toe te voegen onder de reeds bestaande reviews. 
   Hier kun je een [component](https://laravel.com/docs/11.x/blade#passing-data-to-components) van maken. 
3. Zorg dat je de review kunt opslaan bij het betreffende product en na het opslaan moet je weer terugkeren naar de 
   `products.show` pagina.

### Tips

- Bij het aanmaken van het `Component` voor het reviewformulier kun je extra data meegeven. 
  [Documentatie](https://laravel.com/docs/11.x/blade#passing-data-to-components). Let op dat je hier werkt met een 
  `Prop`.
- Het Opslaan van een `Review` doe je in de `store` functie van de `ReviewController`. Maak hiervoor een nieuwe route aan
  in de `web.php` file. En bedenk welke extra informatie je nodig hebt om een review op te slaan.
- Om informatie op te halen uit een formulier gebruik je de `request` class. 
  [Documentatie](https://laravel.com/docs/11.x/requests#retrieving-input). 
- Om een review op te slaan bij een product, heb je het `id` van het product nodig. 
  Wanneer je deze hebt meegegeven in de `store` functie van de `ReviewController`, kun je de review opslaan bij het
  betreffende product. 
- Met de create functie van een Model kun je een nieuwe instantie van een Model aanmaken. 
  [Documentatie](https://laravel.com/docs/11.x/eloquent-relationships#the-create-method)

## Opdracht - Verwijder een Product EN de bijbehorende Reviews

1. Maak een knop in de `products.index` pagina om een product te verwijderen.
2. Wanneer het product verwijderd wordt, moeten ook de bijbehorende reviews verwijderd worden. De database kan
   dit automatisch voor je doen. In de `Migration` gebruik je hiervoor `cascadeOnDelete()`, maar dat kan alleen
   als de `foreign key` [**Constrainted**](https://laravel.com/docs/11.x/migrations#foreign-key-constraints) is.

## Bonusopdracht - Veel-op-veel relatie

Voor de bonusopdracht zorg je ervoor dan een `Product` meerdere `Categories` kan hebben. Een `Category` kan ook bij
meerdere `Products` horen. Voor de functionaliteit betekent dit

- Op de `products.create` pagina kun je meerdere categorieën selecteren d.m.v. checkboxes.
- Op de `products.show` pagina toon je ook de categorieën waar het product bij hoort. Deze kan je eventueel klikbaar 
  maken
- Op de `products.index` pagina kun je filteren op categorieën. Toon alle categorieën en maak deze op dezelfde manier
  klikbaar als op de `products.show` pagina. Als je met een `Component` werkt, kan je deze hergebruiken.

1. Maak een `Category` Model aan met behulp van het
   [Artisan commando](https://laravel.com/docs/11.x/eloquent#generating-model-classes). Maak ook meteen de
   **Migration** en **Resource Controller** aan.
2. Vul de `Migration` aan en voeg een **name** toe. 
3. In dezelfde `Migration` voeg je ook de pivot table toe. Bedenk goed welke foreign keys hierin moeten komen. De naam
   van de pivot table bestaat uit de enkelvoudige vorm van de twee modellen in alfabetische volgorde.
   Deze start je met:
   ```php
       Schema::create('category_product', function (Blueprint $table) {
            // code
       });
   ```
4. Voeg de relaties toe aan de Models `Product` en `Category`. [Laravel documentatie](https://laravel.com/docs/11.x/eloquent-relationships).
5. Maak slim gebruik van Componenten. 
6. Om een categorie bij een product op te slaan, in de store functie, kun je de functie `attach()` gebruiken. 
   [Documentatie](https://laravel.com/docs/11.x/eloquent-relationships#updating-many-to-many-relationships)