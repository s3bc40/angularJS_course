# ***TD AngularJS***

- Importer le repositery : git clone https://github.com/s3bc40/angularJS_course.git
- [Api de AngularJS pour les nuls](https://docs.angularjs.org/api)

## Exercice 1) **Créer une calculette**

* Créer un fichier html et le remplir avec le bout de code ci-dessous

```html
<!doctype html>
<html>
<head>
    <script src="https://ajax.googleapis.com/ajax/libs/angularjs/1.5.6/angular.min.js"></script>
</head>
<body ng-app>
    <div>
        Code à remplir ici
    </div>
</body>
</html>
```

Hints :
- input & ng-model
- {{...}} syntaxe  pour afficher une variable

Rendu:

![Image calculette](https://raw.githubusercontent.com/s3bc40/angularJS_course/master/index/img/calculette.png)

Solution :

[Pour voir la solution cliquez ici !](https://i.ytimg.com/vi/lPEZ6kW7VVA/maxresdefault.jpg)

## Exercice 2) **Découverte des boucles et des filtres**

```html
<!doctype html>
<html>
<head>
  <meta charset="UTF-8">
   <link rel="stylesheet" href="/css/filtreAndScope.css">
</head>

<body ng-app="monApp">

  <div ng-controller="villeNataleCtrl" ng-init="search=''">

    ICI => Première barre de recherche dans un paragraphe

    ICI => Menu déroulant à 3 options : tri par nom/ville/note

<hr>
Classement par ordre croissant:
<hr>
<ol class="columns">
    <div id=colonne1 ng-repeat="on veut parcourir la variable
    comments et associer des filtres directement sur cette boucle">
      <li>
        <strong>USERNAME</strong><br>
        VILLE<br>
        NOTE<br>
      </li>
    </div>
</ol>
  <hr>
  Classement par ordre décroissant:
  <hr>
  MEME CHOSE QU'AVANT MAIS AVEC UN TRI EN SENS INVERSE
<hr>

  </div>
  <script src="https://ajax.googleapis.com/ajax/libs/angularjs/1.6.7/angular.min.js"></script>
  <script>
    var app = angular.module("monApp",[]);
    app.controller('villeNataleCtrl', function ($scope){
      console.log($scope);
      $scope.comments = [
        {
          "username": "Batman",
          "city": "Gotham City",
          "note": 7
        },
        {
          "username": "Superman",
          "city": "Kryptonopolis",
          "note": 18
        },
        {
          "username": "Aquaman",
          "city": "Atlantis",
          "note": 1
        },
        {
          "username": "Deadpool",
          "city": "Sedona",
          "note": 3
        },
        {
          "username": "Iron Man",
          "city": "Seattle",
          "note": 3
        },
        {
          "username": "Spiderman",
          "city": "New-York",
          "note": 6
        },
        {
          "username": "Robin",
          "city": "Gotham City",
          "note": 17
        },
        {
          "username": "Arthur",
          "city": "Kaamelott",
          "note": 4
        },
        {
          "username": "David Goodenough",
          "city": "Atari",
          "note": 2
        },
        {
          "username": "Roparzh",
          "city": "Kaamelott",
          "note": 20
        },
        {
          "username": "Guethenoc",
          "city": "Kaamelott",
          "note": 19
        },
        {
          "username": "Guenièvre",
          "city": "Carmélide",
          "note": 17
        },
        {
          "username": "Léodagan",
          "city": "Carmélide",
          "note": 1
        },
        {
          "username": "Perceval",
          "city": "Pays de Galles",
          "note": 18
        },
        {
          "username": "Bohort",
          "city": "Kaamelott",
          "note": 1
        }
      ];
    });
  </script>
</body>
</html>
```
Hints:
- La barre de recherche est un simple **input** avec **ng-model** comme variable de recherche
- Dans un ng-repeat on peut associer des filtres en séparants les directives par le symbole "**|**"
- Pour l'ordre décroissant il faut ajouter une option au **filtre orderBy**

Rendu :

![Image filtres](https://raw.githubusercontent.com/s3bc40/angularJS_course/master/index/img/angularfiltre.png)


## Exercice 3) **Créez votre controlleur**
```html
<!doctype html>
<html>
    <head>
        <meta charset="UTF-8">
        <link rel="stylesheet" href="/css/filtreAndScope.css">
    </head>

    <body ng-app="monApp">

    <input type="text" ng-model="search">
    <select ng-model="order">
        <option value="name">Organiser par nom</option>
        <option value="attaque">Organiser par attaque</option>
        <option value="PC">Organiser par PC Max</option>
    </select>

    <div ng-controller="pokemonGO">
        <div ng-repeat="pokemon in pokemons | filter:{name:search} | orderBy:order">
            <p>
                <strong>{{pokemon.name}}</strong><br>
                {{pokemon.attaque}}<br>
                {{pokemon.PC}}
            </p>
        </div>
    </div>
    <script src="https://ajax.googleapis.com/ajax/libs/angularjs/1.6.7/angular.min.js"></script>

    <script>
      ECRIRE LE CONTROLLEUR ICI
    </script>
  </body>
</html>
```
Voici un pseudo-pokédex pokémonGO codé avec AngularJS. Le but est de créer le controller **pokemonGO** afin d'afficher le résultat suivant : 

![Image pokedex Go](https://raw.githubusercontent.com/s3bc40/angularJS_course/master/index/img/Screenshot_2018-12-02%20Screenshot.png)

Afin d'obtenir les caractéristiques demandées des pokémons, je vous propose de consulter ce site : [pokeBip.com](https://www.pokebip.com/page__jeuxvideo__pokemon_go__stats_pokemon.html). Au minimum, essayez d'avoir 3 pokémons d'affichés sur votre page web.

Hints : 
- Inspirez vous de l'**exercice 2**pour pouvoir écrire votre controlleur.
- La **liste** sera représenté par [] et les pokémons à l'intérieurs seront des **objets** {}
- Prenez vos pokémons préférés ! 

[Soluce ici pour l'exo](https://memegenerator.net/img/instances/82413744/me-soluce-ici-pour-lexo-you-ouvre-le-lien.jpg)


* Lien vers les solutions please.
  - [Exercice 1)](https://github.com/s3bc40/angularJS_course/blob/master/index/calculette.html)
  - [Exercice 2)](https://github.com/s3bc40/angularJS_course/blob/master/index/filtreAndScope.html)
  - [Exercice 3)](https://github.com/s3bc40/angularJS_course/blob/master/index/pokedex.html)
