# Diapo pour l'oral M2

https://docs.google.com/presentation/d/1vbDEVJkpi1Byvu8XVBpMBsdgFFEwVJprJGpWEwaOuZo/edit?fbclid=IwAR102i31sx7q5hhe0HhEVeH7Yw0FxIHlPGfqZyeS96HImYeD11SARHFbAsc#slide=id.g4a3db9c77a_2_9

# angularJS_course

Course in French on AngularJS. Bioinformatic Master of Bordeaux.

*Ref youtube credits : Grafikart.fr* https://www.youtube.com/watch?v=aBE0St5yI7U&list=PLjwdMgw5TTLUDlJyx4yIPQjoI-w-7Zs1r

## 1.Introduction

**Framework** qui permet de créer des applications JS complexes. SPA (single page application) : application qui fonctionne sur une seule page. Applicationq fluides, navigation facile.  
**Exemple :** client mail = SPA, youtube avec smartTV.

### Pourquoi ?

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

**Attention** : beaucoup de notions compliquées à comprendre

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

Plusieurs formes possibles :

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
  <input type="string" ng-model="search" ng-init="search='cha'">
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

## 3. Controller & Scope

### a) Insights

> Les controllers permettent de **concentrer la logique** de notre application comme dans une structure **MVC** classique. En revanche la notion de Scope est une nouvelle notion."
> 
> Le Scope permet de faire la jointure entre le Controller et la Vue en permettant de transférer les variables dans les 2 sens."  ***Grafikart.fr***

**MVC** = Modèle-vue-contrôleur

> * Un modèle (Model) contient les données à afficher.
>   
>   > * Une vue (View) contient la présentation de l'interface graphique.
>   > >   > * Un contrôleur (Controller) contient la logique concernant les actions effectuées par l'utilisateur.

![MVC](https://upload.wikimedia.org/wikipedia/commons/6/63/ModeleMVC.png)

https://fr.wikipedia.org/wiki/Mod%C3%A8le-vue-contr%C3%B4leur

### b) Le scope

Il permet de faire la liaison entre le Controller et la View.
Pour créer un contrôleur il suffit de créer une fonction qui a n'importe quel nom, mais par
convention un met Ctrl à la fin du nomde la fonction.

Exemple :

```javascript
function monSuperCtrl($scope){
  $scope.users = [
    {
      "username": "Seb",
      "city": "Meaux"
    },
    {
      "username": "Chacha",
      "city": "Toulouse"
    },
    {
      "username": "Ben",
      "city": "Toulouse"
    }
  ];
}
```

On passe en paramètres un scope. Voyons voir comment ça marche sur les exemples précédents !

```html

<body ng-app="monApp">

  <input type="text" ng-model="search">
  <select ng-model="order">
    <option value="username">Organiser par nom</option>
    <option value="city">Organiser par ville</option>
  </select>

    <div ng-controller="villeNataleCtrl">
            <div ng-repeat="comment in comments | filter:{city:search} | orderBy:order">
              <p>
                <strong>{{comment.username}}</strong><br>
                {{comment.city}}
              </p>
            </div>
    </div>
    <script src="https://ajax.googleapis.com/ajax/libs/angularjs/1.6.7/angular.min.js"></script>
    <script>
          var app = angular.module("monApp",[]);
          app.controller('villeNataleCtrl', function ($scope){
          $scope.comments = [
            {
              "username": "Seb",
              "city": "Meaux"
            },
            {
              "username": "Chacha",
              "city": "Toulouse"
            },
            {
              "username": "Ben",
              "city": "Toulouse"
            }
          ];
        });
    </script>
</body>
```

Avec les nouvelles versions de angularJS (>1.3) il faut utiliser une déclaration de variable
du type :

```javascript
angular.module("monApp",[]).controller('monCtrl', function ($scope){code here});)
```

Pour comprendre la notion de scope il faut voir d'autres exemples.
Si l'on créée au niveau du **ng-repeat** un nouvel **input** identique à la barre de recherche,
le scope de ce nouvel input ne sera pas le même que celui de la toute premère barre de recherche.
Alors qu'avec la première barre on peut écrire dans toutes les autres ce n'est pas le cas lorsque l'on est au niveau de la boucle.

## 4. Le module

Garder un système organisé et le rendre réutilisable!

Création d'un module :

```javascript
var app = angular.module("monApp",[]);
app.controller('villeNataleCtrl', function ($scope){
$scope.comments = [
  {
    "username": "Seb",
    "city": "Meaux"
  },
  {
    "username": "Chacha",
    "city": "Toulouse"
  },
  {
    "username": "Ben",
    "city": "Toulouse"
  }
];
});
```

Au niveau de la ligne :

```javascript
var app = angular.module("monApp",[]);
```

Le tableau en paramètre permet d'injecter des dépendances. Il existe des modules pré-existants
qui ne sont pas compris dans angular.min.js comme par exemple **angular-animate.js** . Pour pouvoir importer ce module il suffit d'insérer le script :

```html
<script src="https://code.angularjs.org/angularjs/1.6.7/angular-animate.js"></script>
```

Puis d'écrire :

```javascript
var app = angular.module("monApp",['ngAnimate']);
```

Tips : Utiliser **AngularUI** pour avoir des modules intéressants.

Enfin, il existe une deuxième façon d'écrire la ligne suivante :

```javascript
app.controller('villeNataleCtrl', function ($scope){
  $scope.comments = [
    ...
  ];
  });
```

Pour pouvoir **minifier** (= réduire le code pour qu'il soit plus rapide à traiter par les navigateurs) le code on utilise la notation :

```javascript
app.controller('villeNataleCtrl', [ '$scope', "d'autres noms", function ($scope){
  $scope.comments = [
    ...
  ];
}]);
```

Cela permet d'éviter que les méthodes de minification casse le code.

## 5. Les routes

### a) Les bases

Permet de définir des URLs spécifiques à chaque étape d'une application grâce au module **ngRoute**.

```javascript
var app = angular.module("monApp",['ngRoute']);
app.config(function($routeProvider){
  $routeProvider
  .when('/',{templateUrl: 'partials/home.html'})
  .when('/comments',{templateUrl: 'partials/comments.html'})
  .otherwise({redirectTo: '/'});
});
```

Pour configurer les routes que devra utiliser le fichier initial (généralement **index.html** mais sur github **route.html**) on utilise **app.config($routeProvider){ ... };**.

A partir de là il suffit de donner à **$routeProvider** les actions à mener.
Quand il est à la racine **.when('/',...)** aller à l'URL **'partials/home.html'**.

Pour la deuxième partie on créée dans home.html une référence qui amène aux commentaires.

```HTML
<a href="#!/comments">Voir les commentaires</a>
```

* Remarque : utilisation de **#!** peut être relatif à Windows comme j'ai test sous Windows (dans l'exemple tiré de la vidéo il met seulement **#/comments**)

On peut passer directement le controller en paramètre du .when gérant l'accès à l'url précédente, cela permet de supprimer la **div ng-controller** dans **comments.html**.

### b) Améliorations

Pour améliorer l'apparence de home.html on peut créer un nouvel objet qui contiendra tout un tas de données.

Exemple : Lancer dans JSON generator

```javascript
[
    '{{repeat(5, 10)}}', {
      id: '{{index()}}',
      name: '{{company()}}',
      content: '{{lorem(6)}}',
      comments: [
        '{{repeat(1, 3)}}',{
          username:'{{firstName()}}',
          city:'{{city()}}',
          content:'{{lorem(5)}}'
        }  
      ]
    }
]
`
```

On met l'objet créée dans un nouveau controller :

```javascript
app.controller('PostsCtrl', function($scope){
  $scope.posts = [OBJET ICI]

});
```

Ensuite on modifie **home.html** en :

```HTML
<div ng-repeat="post in posts">

  <h1>{{post.name}}</h1>

  <p>{{post.content}}</p>

  <p>
    <a href="#!/comments">{{post.comments.length}} commentaires</a>
  </p>

  <hr>

</div>
```

Et on ajoute le controller dans **route.html** :

```javascript
.when('/',{templateUrl: 'partials/home.html/',controller:'PostsCtrl'})
```

A ce stade là les commentaires chargés depuis le link ne sont pas ceux de l'objet **$scope.posts** . Si l'on voulait les afficher il faudrait supprimer le controller **'villeNataleCtrl'** et écrire dans home.html :

```HTML
<a href="#!/comments/{{post.id}}">{{post.comments.length}} commentaires</a>
```

Et enfin modifier dans **route.html** :

```javascript
.when('/comments/:id',{templateUrl: 'partials/comments.html/',
controller: 'villeNataleCtrl'})
```

Les commentaires ne s'affichent pas mais c'est normal car nous avons besoin des **services** présentés au chapitre suivant !

### 6. Les services

Lié à la partie "Model" de la structure **MVC**, va permettre de récupérer les données envoyées par différentes sources et de les envoyer dans les **controllers**. Et, les **controllers** vont se charger de renvoyer ces données dans la **View**.

Ces "models" peuvent prendre 3 formats :

* Factory
* Services
* Provider

Ils différents uniquement par leur façon de fonctionner.

On va reprendre l'exemple précédent et résoudre les anciens problèmes liés à l'affichage des commentaires. Pour cela on va utiliser une factory  :

```javascript
// Service Factory
    app.factory('PostFactory', function(){
      var factory = {
        posts : [[OBJET ICI]
          ]
        ],
        getPosts : function() {
          return factory.posts;
        },
        getPost : function(id) {
          return factory.posts[0]
        }
      }
    return factory;
    })
```

L'utilisation de la factory va permettre l'affichage des commentaires par leur id, via le lien créé précedemment. Mais il reste encore à le faire pour tout les lien car actuellement cela ne marche que pour le premier.

Dans la doc, au niveau de **ngRoute**,  au niveau des service il y a **$routeParam** qui permet de récupérer un paramètre. On va donc l'injecter dans l'exemple précédent : 

```javascript
      app.controller('villeNataleCtrl', function ($scope, PostFactory, $routeParams){
        console.log($routeParams)
        $scope.comments = PostFactory.getPost($routeParams.id).comments;
      });
```

De ce fait, on va pouvoir filtrer les id au niveau du **getPost()** de la factory :  

```javascript
        getPost : function(id) {
          var post = {};
          angular.forEach(factory.posts, function(value,key) {
            if(value.id == id ) {
              post = value;
            }
          });
          return post
        }
```

La modification de la méthode **getPost()** va permettre de return un objet contenant les id correspondant au filtre imposé. Ainsi on peut cette fois-ci obtenir les différents commentaires correspondant à l'id de l'objet en optimisant le code : 

```javascript
      app.controller('villeNataleCtrl', function ($scope, PostFactory, $routeParams){
        //console.log($routeParams)
        var post = PostFactory.getPost($routeParams.id);
        $scope.title = post.name;
        $scope.comments = post.comments;
      });
```

Ensuite on fait des modification au niveau de la vue **comments.html** afin d'avoir une vue adéquat (nouveau fichier **comments_serv_.html**) : 

```javascript
<a href="#/">Revenir aux articles</a>

<h1> {{title}} </h1>
<div ng-repeat="comment in comments | filter:{city:search} | orderBy:order">
  <p>
    <strong>{{comment.username}}</strong><br>
    {{comment.city}}
  </p>
</div>
```
L'avantage d'utiliser les factory c'est qu'ont peut les modifier. Maintenant on va voir les différences entre les 3 formats cités précédemment : 

* **Factory** : ça permet de retourner directement ce que l'on retourne dans la fonction. Dans la doc, il n'est plus référencé.
* **Services** : ça permet de retourner directement la fonction, et à chaque appels ça renvoit une nouvelle fonction.
```javascript
    // Services
    app.service('Post', function(){
        that = this;    
            that.posts : [OBJET ICI
            ],
            that.getPosts : function() {
              return that.posts;
            },
            that.getPost : function(id) {
              var post = {};
              angular.forEach(that.posts, function(value,key) {
                if(value.id == id ) {
                  post = value;
                }
              });
              return post
        }
    })

      app.controller('PostsCtrl', function($scope, PostFactory){
        $scope.posts = PostFactory.getPosts();
      });

      app.controller('villeNataleCtrl', function ($scope, PostFactory, $routeParams){
        //console.log($routeParams)
        var post = PostFactory.getPost($routeParams.id);
        $scope.title = post.name;
        $scope.comments = post.comments;
      });
```
On retourne donc l'ensemble de la fonction. L'inconvénient c'est que rien n'est exécuté.
* **Provider** : ça appelle une fonction qui s'appelle **$get** et ça renvoit le résultat de cette fonction. La méthode get permet de faire des opérations (changement de variable d'instances, ou autres).

Ces différents formats permettent une adaptation rapide au différentes librairies existantes.

**Provider** est vraiment intéressant dans le sens où cela fournit un constructeur **$get** qui va permettre de faire des opérations avant même de le charger.

> Créer son propre service permet donc **d'envoyer des informations commune**s entre les différents controleur.


