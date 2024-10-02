# Les 7

Deze les gaat over **SECURITY**. We behandelen de OWASP top 10 en kijken naar de beveiliging van je applicatie.

Bij het opzetten van jouw eigen project hebben we meteen gekozen voor de [Breeze starter kit](https://laravel.com/docs/11.x/starter-kits#laravel-breeze).

_Laravel Breeze is a minimal, simple implementation of all of Laravel's authentication features, including **login**, 
**registration**, **password reset**, **email verification**, and **password confirmation**. In addition, Breeze includes a simple 
"profile" page where the user may update their name, email address, and password._ (Bron: https://laravel.com/docs/11.x/starter-kits#laravel-breeze)

Maar hoe werkt het en waar kan je de verschillende onderdelen vinden? Dit ga je uitzoeken in de 
volgende opdracht.

## Opdracht - Security met Breeze

1. Welke Controllers handelen de verschillende onderdelen van de authenticatie af? En waar staan deze?
2. Zoek uit welke URI's er zijn voor de verschillende onderdelen van de authenticatie. (Gebruik `Artisan`)
3. Waar kan je deze URI's in de code vinden? 
4. Hoe wordt er in de `Views` onderscheid gemaakt tussen een ingelogde en een niet ingelogde gebruiker?
5. Hoe wordt er voor gezorgd dat een `Guest` niet bij `/profile` kan komen?
6. Hoe is de validatie bij login geregeld? Hoe wordt de oude waarde teruggegeven bij een foutieve invoer?
7. Wat is hierin het verschil met `/dashboard` en `/profile`?
8. Hoe zijn formulieren beveiligd tegen Cross-Site Request Forgery (CSRF)? Staat dit op 1 plek?
9. Wat betekenen de `{{ }}` rond een variabele in de Views? Is er een alternatief?
10. Hoe zou je op `role` kunnen controleren, bijvoorbeeld voor het toelaten van een `Admin`?
   
Tips
- Gebruik de documentatie van [Laravel.com](https://laravel.com/docs/11.x/authorization)
- Gebruik de [Laracasts](https://laracasts.com/series/30-days-to-learn-laravel-11) aflevering 20 t/m 23
