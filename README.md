# Documentation

## Convention BEM

* B > Block
* E > Element
* M > Modifier

```html
<!-- mainLit = Block  -->
<ul class="mainList mainList--xmas">
  <!-- __item = Element -->
  <li class="mainList__item">
    <!-- itemLink = Element -->
    <a class ="mainList__itemLink mainList_itemLink--isActive"href ="/home">home</a>
  </li>
  <li class="mainList__item">
    <!-- __itemLink = Element -->
    <a class="mainList__itemLink" href="/home">about</a>
  </li>
  <li class="mainList__item">
    <!-- itemLink = Element -->
    <a class="mainList__itemLink" href="/works">works</a>
  </li>
</ul>
```
```css
.mainList{
  &__item{
    display: flex;
    justify-content: space-between;
    &--xmas{
      background: green;
    }
    &__item{
      list-style: none;
    }
  }
  &__itemLink{
    color: red;
    &--isActive{
      color: white;
    }

  }
}
```
exemple en css
```
.mainList {

}
.mainList--xmas {

}
.mainList__item {

}
.mainList__itemLink {

}
.mainList__itemLink--isActive {

}

```
## Pseudos attributs

Les pseudos attributs `Before`et `after` permettent de créer des noeuds HTML en CSS.
Ils sont essentiellement utilisés pour ajouter des ornements, des décorations ... On peut
bien entendu faire des animations avec , les positionner par rapport à leur parent (relative/absolute).
** Ils doivent etre obligatoirent avoir un `content: ''`**
afin de s'afficher.

```html
<section class="cover">
  <H1 class="cover__mainTitle"> Présentation des pseudo-attributs</H1>
</section>
```
```css
.cover{
  background: #FDFDFD;
  padding: 20px;
  &__mainTitle {
    text-align: center;
    font-size: 24px;
    color: green;
    position: relative;
    &::before,
    &::after,{
      content : '';
      display: block;
      width: 50px;
      height: 50px;
      background : green;
    }
    &::before{
      left: 0;
    }
    &::after{
      right : 0;
    }
  }
}
```


## REM, EM, %, VW Sizing

### %

### EM
* Relative à la taille de son parent direct.
```css
.cover {
<!-- font-size : 16px; 100% = 16px -->
&__mainTitle {
  <!-- 1em = 16px / .8 =/= 12.6px -->
}
}
```

### REM

* Le REM est basé sur la taille de la racine (soit la balises <html>) qui, par défaut a une valeur de 16px. Afin d'éviter tout calcul, il est nécessaire de l'écraser en donnant une base de 10px soit 62,5%.
* Le REM est intéressant à utiliser si les media-queries employées sont en rem également. Cela vous permettra de garder des proportions égales lorsqu'on va redimensionner la page.
* Ses proportions seront également gardées quand l'utilisateur zoomera dans votre page.
```css
html {
  font-size : 62.5%;
}
.mainTitle {
  /* 1.6rem = 16px */
  font-size: 1.6rem;
/* 32rem = 320px */
  width: 32rem;
}
```

### VW(width) / VH(height)

* Unités relatives à la taille de votre écran (peu importe le device)
* Attention au VH et à son contenu. 100vh = 100vh quoi qu'il arrive.
VW : tr_s utile pour les interfaces fluides.

Liens utiles : https://github.com/h5bp/Front-end-Developer-Interview-Questions/tree/master/Translations/French
http://cssnext.io/

### Reset css

* Permet d'anticiper le fait que les navigateurs n'utilisent pas les mêmes padding/margin
* Attention, il faut faire attention à ne pas formater des éléments qui n'en ont pas le besoin (ex: les formulaires avec les border des input)

Lien utile : https://meyerweb.com/eric/tools/css/reset/

* Un framework CSS simple et léger : KNACSS, une feuille de style CSS « reset » sur-vitaminée qui permet de commencer un projet à partir de zéro tout en tenant compte de bonnes pratiques générales (accessibilité, performance, responsive webdesign). Permet de rivaliser avec le reset CSS !

### Bonnes pratiques responsive design

* Avant tout, conserver un corps HTML léger et propre !
* Utiliser les media queries, c'est un usage très simple.
  Connaitre les résolutions -- =< 320px = low resolution, <= 480px = first generation, <= 720px = smartphones, <= 768px = ipad, <= 900px = tablet portrait,
<= 1024px = tablet paysage, >= 1024px = desktop.

Pour en savoir bien plus, un lien utile : https://graphism.fr/10-petits-conseils-pour-le-responsive-web-design/

### Centrer un bloc...

```css
p.blocktext {
    margin-left: auto;
    margin-right: auto;
    width: 6em
}
```

```html
<p class="blocktext">Cet étroit bloc de texte est centré. Notez que les lignes à l'intérieur du bloc ne sont pas centrées (elles sont alignées à gauche).</p>
```

### ...ou une image

```css
img.displayed {
    display: block;
    margin-left: auto;
    margin-right: auto;
  }
```

```html
<img class="displayed" src="..." alt="...">
```

### Connaître !important
N'importe quel style marqué avec !important va être directement appliqué au-dessus d'un autre qui viendrait normalement s'appliquer.

```css
.page {
  background-color:blue !important;
  background-color:red;
}
```

Dans cet exemple, `background-color:blue;` sera pris en compte car il est marqué `!important`, même s'il y a un `background-color:red;` derrière lui. `!important` est donc utilisé afin de forcer l'application d'un style si un autre arrive derrière lui, cependant cela peut ne pas fonctionner sur Internet Explorer.

### Envie d'inspiration?

Si vous êtes à la recherche de jolis designs en pur CSS pour vous inspirer, voici quelques sites intéressants:

https://cssremix.com/

http://www.cssmania.com/

http://www.cssleak.com/

### Petit conseil pour améliorer son référencement

L’information n’attends pas et Google indexe toujours plus vite... Si vous éditez un blog ou un site dont vous datez les articles, vous aurez surement remarqué que, suite à son indexation dans Google, sous le titre de votre page et juste avant le début de sa description, dans la page des résultats, apparaît la date de publication (et non d’indexation) de votre article.

```html
<p>Posté le <time datetime="2010-11-29">29.11.2010</time>.</p>
```

### Les keyframes c'est quoi?


La règle `@keyframes` spécifie le code d'animation.

L'animation est créée en changeant graduellement d'un ensemble de styles CSS pour un autre.

Pendant l'animation, vous pouvez modifier l'ensemble des styles CSS plusieurs fois.

Précisez quand le changement de style aura lieu en pourcentage, ou avec les mots-clés "from" et "to", qui sont les mêmes que 0% et 100%. 0% est le début de l'animation, 100% est lorsque l'animation est terminée.

Voici un exemple d'utilisation :

```css
@keyframes myexample {
    0%   {top: 0px; left: 0px; background: red;}
    25%  {top: 0px; left: 100px; background: blue;}
    50%  {top: 100px; left: 100px; background: yellow;}
    75%  {top: 100px; left: 0px; background: green;}
    100% {top: 0px; left: 0px; background: red;}
}
```
