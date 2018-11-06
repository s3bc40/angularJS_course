# angularJS_course
Course in French on AngularJS. Bioinformatic Master of Bordeaux.

*Ref youtube credits : Grafikart.fr* https://www.youtube.com/watch?v=aBE0St5yI7U&list=PLjwdMgw5TTLUDlJyx4yIPQjoI-w-7Zs1r

## 1.Introduction
**Framework** qui permet de créer des applications JS complexes. SPA (single page application) : application qui fonctionne sur une seule page. Applicationq fluides, navigation facile.  
**Exemple :** client mail = SPA, youtube avec smartTV.

###Pourquoi ?
Gestion de l'historique, données en AJAX avec des callback : sans framework c'est compliqué (notamment en JS avec la gestion d'objets). Le code serait difficile à lire, et non maintenable.
Framwork : structure déjà conçu et adapté au navigateur.

**Approche de AngularJS :** automatisation de certaines fonctionnalités qui permet faciliter l'écriture de l'application SPA. Mais le comportement automatique peut être contraignant ("pimpage" compliqué).

```html
<!doctype html>
<html ng-app>
<head>
    <script src="https://ajax.googleapis.com/ajax/libs/angularjs/1.5.6/angular.min.js"></script>
</head>
<body>
    <div>
        <label>Name:</label>
        <input type="text" ng-model="yourName" placeholder="Enter a name here">
        <hr>
        <h1>Hello {{yourName}} !</h1>
    </div>
</body>
</html>
```
> Philosophie de AngularJS : rendre le html dynamique ! Modifcation d'attributs, de balises et ajout de nouvelles balises.

**Attention** : beaucoup de notion compliqué à comprendre
+ Binding
+ MVC
+ Routing
+ Linking
+ Scope
+ Transclusion
+ Directive
+ Prototype

## 2.Les directives
```html
<!doctype html>
<html ng-app><!-- ngapp = directive -->
<head>
    <script src="https://ajax.googleapis.com/ajax/libs/angularjs/1.5.6/angular.min.js"></script>
</head>
<body>
    <div>
        <label>Name:</label>
        <input type="text" ng-model="yourName" placeholder="Enter a name here"><!-- ng-model = directive -->
        <hr>
        <h1>Hello {{yourName}} !</h1><!-- directive -->
    </div>
</body>
</html>
```

> C'est une propriété de AngularJS qui permet d'injecter des comportement dans le code HTML.

Plusieurs formes possible : 
+ attribut HTML
+ élément HTML
+ class

**POWER-UP HTML :D** sans ajouter de Js.

### a) Petits travaux
+ **ng-app :** permet de placer l'application développée.
+ **ng-model :** valeur stockée dans une variable donnée.

*Faire une calculatrice :*
```html
<!doctype html>
<html>
<head>
    <script src="https://ajax.googleapis.com/ajax/libs/angularjs/1.5.6/angular.min.js"></script>
</head>
<body ng-app>
    <div>
        <input type="number" ng-model="nb1">
        <input type="number" ng-model="nb2">
        {{"Somme :" + (nb1 * 1 + nb2 * 1)}}
    </div>
</body>
</html>
```
+ **ng-init :** injecter les données directement dans le code HTML.
+ **ng-repeat :** équivalent à un for each pour parcourir une liste.

*Qui a commenté dans l'ordre ? :*
```html
<!doctype html>
<html>
<head>
</head>
<body ng-app>
    <div ng-init="users=['Benoit','Charlotte','Seb']">
        <ul>
            <li ng-repeat="user in users">{{user}}</li>
        </ul>
    </div>
    <input type="number" ng-model="nb1">
    <script src="https://ajax.googleapis.com/ajax/libs/angularjs/1.5.6/angular.min.js"></script>
</body>
</html>
```

### b) Les filtres

Vidéo 2 : 8:17

Utilité :

+ **Modifier** les variables
+ **Organiser** des éléments
+ **Filtrer** des données

Exemple :

+ **uppercase** : mettre en majuscule => utilisation du **|** importante !

```html
<!doctype html>
<html>
<head>
</head>
<body ng-app>
    <div ng-init="users=['Benoit','Charlotte','Seb']">
        <ul>
            <li ng-repeat="user in users">{{user | uppercase}}</li>
        </ul>
    </div>
    <input type="number" ng-model="nb1">
    <script src="https://ajax.googleapis.com/ajax/libs/angularjs/1.5.6/angular.min.js"></script>
</body>
</html>
```
+ **filter** : permet de filtrer un array, une string ou une fonction (voir doc)

```html
<!doctype html>
<html>
<head>
</head>
<body ng-app>
  <input type="number" ng-model="search">
    <div ng-init="users=['Benoit','Charlotte','Seb']">
        <ul>
            <li ng-repeat="user in users | filter:search">{{user | uppercase}}</li>
        </ul>
    </div>
    <script src="https://ajax.googleapis.com/ajax/libs/angularjs/1.5.6/angular.min.js"></script>
</body>
</html>
```

=> Dans cet exemple on peut écrire dans une box pour afficher ce qui match avec l'input

+ **orderBy** : trier les données par ordre croissant d'un ou plusieurs

```html
<!doctype html>
<html>
<head>
</head>
<body ng-app>

  <input type="number" ng-model="search">
  <select ng-model="order">
    <option value="username">Organiser par nom</option>
    <option value="says">Organiser par paroles</option>
  </select>

    <div ng-init="users=[{username:'Benoit', says:'Mon petit oiseau...'},{username:'Charlotte', says:'A pris sa volée...'},{username:'Seb', says:'A la volette...'}]">
            <div ng-repeat="user in users | filter:{says:search} | orderBy:order">
              <p>
                <strong>{{user.username}}</strong><br>
                {{user.says}}
              </p>
            </div>
    </div>
    <script src="https://ajax.googleapis.com/ajax/libs/angularjs/1.5.6/angular.min.js"></script>
</body>
</html>
```
=> Ici, on peut trier grâce au menu déroulant **select** et filtrer avec le menu de recherche **input**. On display le nom de l'utilisateur et sa citation !
