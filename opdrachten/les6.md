# Les 6

In deze les gaan we in een nieuw project starten met het maken van relaties tussen modellen. We gaan kijken naar de
volgende relaties en passen deze toe in een voorbeeld project

- 1-op-veel
    - `Product` heeft meerdere `Reviews`
    - `Review` hoort bij één `Product`
- Veel-op-veel
    - `Product` heeft meerdere `Categories`
    - `Category` hoort bij meerdere `Products`

Vorig jaar hebben we gezien dat bij een 1-op-veel relatie het nodig was om een **foreign key** toe te voegen aan de tabel.
Voor de veel-op-veel relatie hebben we een andere oplossing nodig en dat is een **pivot table** of **koppeltabel**.
Bij het aanmaken van de database moeten we hier dus rekening mee houden.

## Opdracht - ERD

Maak het ERD voor het voorbeeldproject op papier of in een app naar keuze (zoals [Miro](https://miro.com/nl/),
[Lucidchart](https://www.lucidchart.com/pages/landing) of [draw.io](https://www.drawio.com/)).

- **Teken** de 1-op-veel relatie tussen `Product` en `Review`
- **Teken** de veel-op-veel relatie tussen `Product` en `Category`

## Opdracht - Maken `Product` Model

1. Maak `Product` Model aan  met behulp van het
   [Artisan commando](https://laravel.com/docs/11.x/eloquent#generating-model-classes). Maak ook meteen de
   **Migration** en **Resource Controller** aan.
2. **Voeg** de benodigde velden toe aan de Migrations die je nodig hebt.
3. Maak de `index`, `create`, `show` pagina's. 
4. Let er bij het uitwerken van de createpagina op dat je niet zomaar data mag toevoegen aan de database. 
   In het Model bepaal je wat mag  en niet mag. En dat bepaal je met de property `$fillable` in het 
   [Model](https://laravel.com/docs/11.x/eloquent#mass-assignment).

## Opdracht - Maken `Review` Model

1. Maak `Review` Model aan met behulp van het
   [Artisan commando](https://laravel.com/docs/11.x/eloquent#generating-model-classes). Maak ook meteen de
   **Migrations** en **Controller** aan (dus geen Resource Controller).
2. Vul de Migration en voeg de **foreign keys** toe aan de Migrations voor de 1-op-veel relatie. Dit doe je door een 
   veld toe te voegen met `foreignIdFor()`. Zie [Laravel documentatie](https://laravel.com/docs/11.x/migrations#column-method-foreignIdFor)
3. Koppel de `Review` aan de `Product` in het `Model`. Kies hiervoor de juiste relatie in de 
   [Laravel documentatie](https://laravel.com/docs/11.x/eloquent-relationships).
4. Maak je een foutje met een `Migration`. Je kunt altijd een stap terug met het volgende commando. Let op je moet
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

1. Zorg ervoor dat je in de `products.show` pagina de reviews van het product toont.
2. Maak een formulier aan om een review toe te voegen onder de reeds bestaande reviews. 
   Maak hiervan een [component MET Class](https://laravel.com/docs/11.x/blade#passing-data-to-components). 
3. Zorg dat je de review kunt opslaan bij het betreffende product en na het opslaan moet je weer terugkeren naar de 
   `products.show` pagina.

### Tips

- Bij het aanmaken van het `Component` voor het Review formulier kun je extra data meegeven. 
  [Documentatie](https://laravel.com/docs/11.x/blade#passing-data-to-components). Let op dat je hier werkt met een 
  `Prop`.
- Het Opslaan van een `Review` doe je in de `store` functie van de `ReviewController`. Maak hiervoor een nieuwe route aan
  in de `web.php` file. En bedenk welke extra informatie je nodig hebt om een review op te slaan.
- Om informatie op te halen uit een formulier gebruik je de `request` class. 
  [Documentatie](https://laravel.com/docs/11.x/requests#retrieving-input). 
- Om een review op te slaan bij een product, heb je het `id` van het product nodig. 
  Wanneer je deze hebt meegegeven in de `store` functie van de `ReviewController`, kun je de review opslaan bij het
  betreffende product. Je zal de data wel eerst moeten 
  [mergen](https://laravel.com/docs/11.x/requests#merging-additional-input)
- Met de create functie van een Model kun je een nieuwe instantie van een Model aanmaken. 
  [Documentatie](https://laravel.com/docs/11.x/eloquent-relationships#the-create-method)
