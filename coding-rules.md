# fontEnd Coding Rules
- [CSS](#css)
- [HTML](#html)
- [Accessibilité](#accessibilité)
## CSS
### Généralités
- L'encodage des fichiers et des bases de données doit se faire en UTF-8 (sans BOM).
- Le code CSS produit doit être valide selon les normes ([http://jigsaw.w3.org/css-validator/](http://jigsaw.w3.org/css-validator/))
- Couleurs en codes hexadécimaux minuscules.
- Les classes utilisées comme ancre JS doivent être préfixés par‘js-’(js-class-name).
- Commentaires en français.
- margin padding et font en unités rem.
- Privilégier les syntaxes via propriété raccourcies :
```css
/* non */
.my-class {
    margin-top : 2rem ;
    margin-right : 3rem ;
    margin-bottom : 2rem ;
    margin-left : 3rem ;
    padding-top: 5rem;
    padding-right: 10rem;
}
/* oui */
.my-class {
    margin : 2rem 3rem ;
    padding : 5rem 0 0 10rem ;
}
```
- L'unité est inutile si la valeur est nulle. Ne pas donner d'unité à line-height ([référence](http://allthingssmitty.com/2017/01/30/nope-nope-nope-line-height-is-unitless/ "référence")) :
```css
/* non */
.my-class {
    margin: 0px;
    font-size: 0.9rem;
    line-height: 2em;
    border: none;
}
/* oui */
.my-class {
    margin: 0;
    font-size: 0.9rem;
    line-height: 2;
    border: 0;
}
```
        
        
- Ne pas ajouter des styles dans normalize.css.
- niveau maximal d'imbrication à 2.
### Généralités
- Les indentations se font à l'aide de deux espaces et sous forme de tabulations.
- Les propriétés CSS sont rédigées ligne par ligne dans chacun des blocs.
- Un espace sépare le nom de la propriété de sa valeur, après les `:`. Un espace sépare le sélecteur du bloc avant la première accolade `{`.
- Les déclarations sont ordonnées par ordre alphabétique .
```css
/* exemple de syntaxe */
.my-class {
    background: #000;
    color: #fff;
}
```
### Sélecteurs CSS
Le choix des sélecteurs CSS doit se faire en priorité pour leur pertinence et leur maintenabilité.
Ainsi, il est indiqué de pouvoir cibler n'importe quel élément indépendamment de son contexte : si l'élément doit être déplacé de son contexte, tel un module ou un composant, les styles devraient toujours s'appliquer.
- Méthodologie BEM à privilégier ([http://getbem.com/introduction/](http://getbem.com/introduction/)).
- Nommage en anglais.
- Interdiction de styles en ligne dans les tags HTML.
- Interdiction de styler avec des id's.
- Interdiction de styler les ancres pour le JS.
- Classes séparées par des tirets :
```css
/* non */
.myClass {
    ...
}
/* oui */
.my-class {
    ...
}
```
- Éviter de surcharger un sélecteur, car cela lui ajoute du poids inutilement : 
```css
/* non */
ul.nav li a.my-class {
    …
}
/* oui */
.my-class {
    …
}
```
- Éviter les sélecteurs associés à la structure HTML, un élément doit pouvoir être ciblé quel que soit son conteneur ou son emplacement dans le DOM: 
```css
/* non */
div > h1 + p {
    …
}
/* oui */
.my-class {
    …
}
```
- Éviter d'écraser une règle par une autre:
```css
/* non */
li {
    visibility: hidden;
}
li:first-child {
    visibility: visible;
}
/* oui */
li:not(:first-child) {
    visibility: hidden;
}
```
#### Documentations
- [bem-methodology-for-small-projects](https://www.smashingmagazine.com/2014/07/bem-methodology-for-small-projects/ "bem-methodology-for-small-projects")
- [en.bem.info/methodology](https://en.bem.info/methodology "en.bem.info/methodology")
- [guidecss.fr/convention.html](http://guidecss.fr/convention.html "guidecss.fr/convention.html")
- [www.stubbornella.org/content/2010/06/25/the-media-object-saves-hundreds-of-lines-of-code](http://www.stubbornella.org/content/2010/06/25/the-media-object-saves-hundreds-of-lines-of-code "www.stubbornella.org/content/2010/06/25/the-media-object-saves-hundreds-of-lines-of-code")
- [thesassway.com/advanced/modular-css-naming-conventions](http://thesassway.com/advanced/modular-css-naming-conventions "thesassway.com/advanced/modular-css-naming-conventions")
- [nicolasgallagher.com/about-html-semantics-front-end-architecture](http://nicolasgallagher.com/about-html-semantics-front-end-architecture "nicolasgallagher.com/about-html-semantics-front-end-architecture")
### Architecture SCSS
**base/** Code standards du projet, règles de typographie sur les balises standards (body, hn…).<br />
**helpers/** Regroupe les outils et helpers Sass utilisés à travers le projet. Toutes les variables globales, les fonctions, les mixins, ...<br />
**Layout/**  Les éléments du gabarit (header, footer, navigation, sidebar…).<br />
**modules/** Les composants à réutiliser à volonté partout dans le site.<br />
**routers/** Regroupe les fichiers principaux. Ces fichiers ne doivent contenir que des `@import`.<br />
**themes/** Gère les différents thèmes du site.<br />
**vendors/**  Regroupe tous les fichiers CSS provenant de bibliothèques et frameworks externes.<br />
*****
## HTML
- L'encodage des fichiers et des bases de données doit se faire en UTF-8 (sans BOM).
- Les indentations se font à l'aide de quatre espaces à l'aide de tabulations.
- Choisir des noms en anglais prioritairement (fichiers, images, etc.).
- Les noms d'éléments et des attributs sont rédigés en minuscules.
- Les valeurs identiques aux attributs ne sont pas renseignées sauf nécessité (ex. en HTML5 pas de checked="checked").
- Le nom des fichiers se fait en PascalCase.
- Usage des double quotes autour des valeurs d'attributs (ex. `class="my-class"`).
- Les éléments HTML5 `<header>`, `<article>`, `<main>`, `<footer>`, `<aside>`, `<section>` et `<nav>` sont privilégiés aux éléments neutres `<div>` si leur fonction s'y prête.
- Nombre de classes appliquées à un élément limité à 4.
- Toujours utiliser `rel="noopener noreferrer"` sur des liens `target="_blank"`
*****
## Accessibilité
Une attention toute particulière sera apportée à l'accessibilité des documents afin que chaque utilisateur, quelle que soit sa défaillance, puisse avoir plein accès aux contenus proposés.
### Documentations 
- [DISIC/guide-integrateur](https://github.com/DISIC/guide-integrateur "DISIC/guide-integrateur")
- [Web Accessibility Initiative - WAI](https://www.w3.org/WAI/standards-guidelines/aria/ "Web Accessibility Initiative - WAI")
- [accede-web - La démarche accessibilité](https://www.accede-web.com/ "accede-web - La démarche accessibilité")
- [Atalan - Blog accessibilité numérique](https://blog.atalan.fr/ "Atalan - Blog accessibilité numérique")
- [The A11Y Project](https://a11yproject.com/ "The A11Y Project")
- [access42.net/blog](https://access42.net/blog "access42.net/blog")
### Généralités
- Ne pas fixer de hauteur sur les éléments afin que le contenu reste lisible lorsque le texte est zoomé.
- Respecter la hiérarchie des titres `<hX>`.
- Ne pas supprimer l'outline autour des éléments cliquables (pas de `outline: none`).
- Utiliser les éléments HTML pour leur fonction/sémantique et non pas pour leur forme.
- Utiliser les éléments pouvant recevoir le focus (`<a>`, `<input type="button">`) lorsqu'ils sont cliquables/interactifs.
- Ne jamais utiliser `display: none` ou `visibility: hidden` pour masquer visuellement du texte qui devrait être retranscrit par un lecteur d'écran. Utiliser la classe `.sr-only`.
- Tous les liens doivent avoir un intitulé, un lien "vide" n'est pas accessible.
- Signaler lorsqu’un lien s’ouvre dans une nouvelle fenêtre :
`<a href="URL" target="_blank" aria-label="Lire l’article (nouvelle fenêtre)">Lire l’article</a>`.
- Chaque image doit avoir un attribut `alt`. Les images décoratives (qui n'apportent rien au contenu) doivent avoir un attribut alt vide `<img ... alt="">`.
- Une image porteuse d'information ou cliquable doit avoir une alternative textuelle, l'attribut `alt` doit reprendre l'information figurant sur l'image.
