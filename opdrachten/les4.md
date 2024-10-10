# Les 4

## Basis View en Component

Bekijk de Laracast video's over het aanmaken van een simpele app met 3 pagina's. Je leert 
wat een `View` is en hoe je een `Component` aanmaakt. Maak ook de **opdracht** die wordt
gegeven in de vorm van huiswerk.

## Opdracht

> **_NOTE: Gebruik hiervoor een oefenproject zonder Breeze._**
>
> Heb je nog geen 'kaal' oefenproject? Maak deze dan weer aan met `artisan` commando in een nieuwe map. Je hoeft het project niet toe te voegen aan GIT, mag natuurlijk wel.
>
> ```composer create-project laravel/laravel .```

Bekijk de volgende video's van [Laracast](https://laracasts.com/): _30 days to learn laravel 11_ 
- [Episode 2](https://laracasts.com/series/30-days-to-learn-laravel-11/episodes/2)
- Maak de opdracht van Episode 2
- [Episode 3](https://laracasts.com/series/30-days-to-learn-laravel-11/episodes/3)
- Maak de opdracht van Episode 3

- Ga, in het oefenproject, aan de slag met Layouts.
- Zorg voor een dynamische navigatie met actieve links. Werk met Components en Partials
- Maak een lijstje met informatie en stuur deze mee aan een `View`. Toon deze d.m.v. een `loop`. De items in de loop zouden een `Component` kunnen zijn.
- Informatie op [Laravel.com](https://laravel.com/docs/11.x), [**naslag rond Components**](components.md) en [Laracast](https://laracasts.com/series/30-days-to-learn-laravel-11/)
  
> **Tip!** Maak gebruik van `dd()` en `dump()` als je wilt debuggen. Je kunt dit ook in een view gebruiken maar dan met `@dd()` en `@dump()`

## Opdracht

> **_Note: Voor deze opdracht maak je gebruik van het project voor de eindopdracht._**

Bij het aanmaken van een nieuw Laravel project heb je voor je eigen project gekozen voor Breeze. Een bezoeker kan zich 
dus registreren en inloggen. 

Voor de onderstaande opdrachten maak je gebruik van de documentatie over [Blade Templates](https://laravel.com/docs/11.x/blade).
- Zorg in een view ervoor dat je het verschil ziet tussen een ingelogde en een niet ingelogde gebruiker op een eigen gemaakte pagina. 
- Maak onderdelen alleen zichtbaar voor ingelogde gebruikers.
- Ga ook hier aan de slag met `Components` en zet de layout en navigatie naar je eigen hand.

> **Tip!** Wanneer je aanpassingen wilt doen in de css, voer dan het volgende commando uit in een tweede terminal venster: `npm run dev`

