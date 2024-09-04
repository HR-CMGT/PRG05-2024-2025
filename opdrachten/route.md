# Routes

## Wat is een router?
Een router delegeert de input die via een URL binnenkomt naar de juiste code (een controller) binnen je project.

Bij het [aanmaken van een nieuw project](../instructies/new-project-and-route.md) heb je de router al in actie gezien. Om een bepaalde URL af te vangen
en door te sturen naar een controller, maak je gebruik van routes.
Door bijvoorbeeld de volgende route toe te voegen aan `web.php`
```php
Route::get('/about-us', function() {
   return 'This page is about us';
});
```
zal de volgende URL: `http://localhost:8000/about-us` de tekst `This page is about us` tonen.

Het keyword 'get' na de dubbele punt geeft de actie aan. 

### Opdracht 

- Maak een route voor de 'contact' pagina
- Laat de route een view tonen met contactinformatie

### Opdracht 
- Zoek uit welke andere optie er mogelijk zijn achter de dubbele punt en wat deze betekenen.

## Informatie meegeven aan de View 

Bij het [aanmaken van een nieuw project](../instructies/new-project-and-route.md) heb je ook een view (`about-as.blade.php`) aangemaakt in de map `resources/views`. 
Om deze view te tonen gebruikte je de code

  ```php
  Route::get('/about-us', function() {
      return view('about-us');
  });
  ```
Om extra informatie mee te geven aan de view, kun je een tweede parameter (een `array`) meegeven aan de `view()` functie.
Hiervoor maak je eerst een variabele aan boven het return statement en daarna stuur je deze door in de `view()` functie.

  ```php
  Route::get('/about-us', function() {
      $company = 'Hogeschool Rotterdam';
      return view('about-us', [
          'company' => $company
      ]);
  });
  ```

In de view kun je de variabele `company` nu gebruiken. Dit doe je door de variabele tussen dubbele accolades te plaatsen in de HTML.

  ```html
    <h1>About {{$company}}</h1>
    <p>Lorem ipsum...</p>
  ``` 

### Opdracht 

- Maak bovenstaande werkend in jouw project

## Parameter toevoegen aan een Route

Als je extra informatie wilt doorgeven via een route zoals: https://localhost:8000/products/macbook, waar "macbook" de 
extra informatie is die je wilt doorgeven. Dan kan je dit doen door een parameter toe te voegen aan de route.


- Maak een nieuwe route aan in `web.php` met `{ }` om de parameter aan te geven
    
  ```php
    Route::get('products/{name}', function() {
        // code
    });
  ```
  
Dit kun je natuurlijk ook doen voor een id of een andere parameter die je wilt doorgeven.

### Opdracht 

- Maak een route aan die een id doorgeeft
- Maak een View waarin het id getoond wordt
- Verander het id in de URL en bekijk het resultaat in de browser

## Named Routed

In applicaties komen links veel voor. In een Laravel applicatie kun je in de HTML een direct link maken naar een andere pagina. 
Bijvoorbeeld naar detailpagina van een product: `http://localhost:8000/products/productdetails/24`. Het gebeurt echter regelmatig
dat URL's worden aangepast. In dat geval zou je overal deze directe links moeten aanpassen. De oplossing hiervoor is 
het gebruik van [named routes](https://laravel.com/docs/11.x/routing#named-routes).

### Opdracht 

- Maak een named route aan voor de route die je in opdracht 1 hebt gemaakt
- Gebruik de named route in de view van de Homepagina en test of het werkt
- Verander de URL in de route en bekijk of de link nog steeds werkt

### Opdracht 

- Zoek uit hoe optional parameters werken in Laravel en maak een werkend voorbeeld. 
- Test je voorbeeld door zowel de route met als zonder parameter te bezoeken.

# Controllers

### Opdracht

- Maak een nieuwe controller aan met de naam `AboutUsController`
- Zorg dat de `about-us` view getoond wordt door de controller. Zoek uit hoe je vanuit de route (`web.php`) de controller aanroept.
- Zoek uit hoe je extra informatie naar de `controller` kunt sturen die opgevangen is in de `route`. Vervolgens geef je deze informatie door aan de `view`.

## Resource Routes

Resource routes en controllers zijn een handige manier om snel CRUD (Create, Read, Update, Delete) op te zetten 
binnen je Laravel applicatie. 

- in terminal `php artisan make:controller`
- Voer de naam _ProductController_ in
- type: kies **Resource**
- model **empty** (voor nu)
- Ga naar de `ProductController` 

Je ziet dat er al een aantal functies zijn aangemaakt. Deze functies zijn de standaard functies die je nodig hebt voor CRUD operaties. 

- Verander de index functie in de `ProductController` naar:
    ```php
    public function index()
    {
        return view('products.index');
    }
    ```

- Maak een view aan voor index (ALT + Enter on `'products.index'`) en voeg HTML toe.
- Go to [localhost:8000/products](http://localhost:8000/products) 
- _Waarom laat dit een 404 foutmelding zien?_


  **Add resource routes**

- Ga naar `web.php` en voeg de volgende regel toe:
    ```php
    Route::resource('products', ProductController::class);
    ```

Met deze ene regel code worden alle routes aangemaakt die je nodig hebt voor CRUD operaties.

Resource routes hebben standaard ingebouwde [parameters](https://laravel.com/docs/11.x/controllers#actions-handled-by-resource-controller).