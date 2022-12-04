# Wiki Design Pattern : Groupe C
## Objet Composite et Injection de contrôle / de dépendance

Dans ce wiki nous allons vous présenter et expliquer les design patterns suivants : 
* [L'objet Composite](#objetComposite) 
* [L'injection de contrôle / de dépendance](#injection)

Nous allons suivre un plan précis pour chacun d'entre eux afin que ce soit clair, net et pertinent. Nous allons utiliser le plan suivant : 
1. Concept / Définition 
2. Pour quel problème ? ([Composite](#problemeComposite) | [Injection](#problemeInjection))
3. Avantages et Inconvénients ([Composite](#aiComposite) | [Injection](#aiInjection))
4. Exemple ([Composite](#exempleComposite) | [Injection](#exempleInjection))

### Introduction

L’objet Composite et l'injection de contrôle sont les noms de design patterns, ou patron de conception en français. Les designs patterns sont des solutions aux problèmes récurrents dans la conception d'applications orientées objet. Le patron de conception décrit les grandes lignes d'une solution, qui peuvent ensuite être modifiées et adaptées en fonction des besoins. Il existe au total 23 designs patterns différents, ils sont tous triés dans 4 familles : 
* De **construction** → description de la manière dont un objet peut être créé et isolation du code relatif à la création 
* De **structuration** → description de la manière dont doivent être connectés les objets de l'application afin de rendre ces connexions indépendantes de futures évolutions 
* De **comportement** →  description de comportements d'interaction entre objets
Autres → contient tous les autres design patterns ne faisant pas parti des 3 autres familles 

Ce concept de design pattern est apparu dans les années 90, suite à la publication d'un ouvrage en 1995 par une équipe composée de **Erich Gamma, Richard Helm, Ralph Johnson et John Vlissides** . Ce livre s’intitule _"Design Patterns : Elements of Reusable Object-Oriented Software"_. Nous pouvons y retrouver les 23 Design Patterns dédiés au développement logiciel évoqués précédemment.

------------------------------------------------------------------------------------------------------------------------------------
### Objet Composite <a id="objetComposite"></a> 

Dans cette partie, nous nous intéresserons uniquement au design Pattern nommé  **“Objet Composite”**, l’idée transmise est de représenter des objets simples ainsi que leurs récipients ou compositions (c’est-à-dire des compositions d’objets) dans une classe abstraite afin de pouvoir les traiter de manière uniforme. En effet , ce design pattern permet de gérer un ensemble d'objets en tant qu'un seul et même objet, en d'autres termes un objet composé de plusieurs autres. Pour illustrer ce concept et faciliter l’explication , nous avons utiliser un diagramme UML ( récupérer sur : https://fr.wikipedia.org/wiki/Composite_(patron_de_conception))  : 
<p align="center">
  <img src="https://www.cjoint.com/doc/22_12/LLbiZfMmdPS_Capture-d’écran-2022-12-01-à-09.35.15.png" alt="Diagramme UML Objet Composite"/>
</p>

Nous pouvons donc observer ce diagramme UML représentant l’idée développée par le pattern. 
Le **“Composant”** représente ici une interface qui définit les comportements / opérations commun(e)s de chaque composants (feuille et composite) dans l’arborescence. 

Ensuite nous avons le **“Composite”** (conteneur en francais) , c’est un élément composé de sous-éléments : feuilles ou autres conteneurs. Un conteneur n'a aucune connaissance des classes de ses enfants. Il interagit avec via l'interface du composant. Lorsqu'il reçoit une demande, le conteneur délègue des tâches à ses enfants, traite les résultats intermédiaires et renvoie le résultat final. 

Enfin , nous avons la **“Feuille”**, qui représente les composants n’ayant pas de sous-éléments , elle reprend aussi le comportement par défaut défini dans l'interface.
Nous pouvons affirmer que ce design pattern suit une structure d'arborescence avec une interface , un conteneur et les enfants (pouvant être des conteneurs aussi). 

### Pour quel problème ? <a id="problemeComposite"></a>

Le but principal d’un design pattern est de fournir une solution a un **problème récurrent** lors de la conception et du développement de logiciel, application. Le composite pattern a été mis en place pour résoudre des problèmes sur applications dont la structure principale peut être représentée sous la forme d’**une arborescence**. 

Le résultat recherché de par l'utilisation de ce pattern est un logiciel le plus flexible possible et caractérisé par des objets faciles à mettre en œuvre, testables, interchangeables et réutilisables. Le pattern composite décrit une façon de traiter de la même manière les objets simples et composites. Il est ainsi possible de créer des structures d'objets faciles à comprendre et permettant l'accès le plus efficace. Cela minimise également la tendance aux erreurs du code.

De ce fait, nous pouvons affirmer que le design pattern composite est très utile et résout de nombreux problèmes rien qu'avec l’utilisation de celui-ci. Mais, nous pouvons imaginer que ce pattern comporte non seulement des avantages mais probablement aussi quelques inconvénients que nous allons pouvoir étudier. 

### Avantages et inconvénients <a id="aiComposite"></a>

Nous allons désormais vous présenter les quelques avantages et inconvénients que rencontre ce design pattern, même minime. Les avantages reste plus important que le nombre d'inconvénients.  Tout d’abord, ce pattern permet de gérer des structures fortement imbriquées. En effet , si la structure suit l’organisation en arborescence alors, qu’il s’agisse d’un objet primitif ou composite, avec des dépendances simples ou complexes : **la profondeur et la largeur de l’imbrication** n’ont pas d’importance pour le modèle de conception composite. 

Ensuite, les différences entre **les types d'objets** peuvent être complètement ignorées par les clients, de sorte qu'aucune fonction n'est nécessaire pour l'accès. L'avantage est que le code client reste simple et léger. 

Enfin, le dernier point fort de ce pattern est que la structure est **flexible** et l’**agrandissement** de celle-ci est très simple. En effet, l’ajout de nouvelles “feuilles” ou de nouveaux objets est très simple et ne nécessite pas forcément de modification du code. 

Malgré ses avantages , nous pouvons citer deux inconvénients au pattern  : 

* La **mise en place de l’interface** est plutôt compliquée : il faut décider quelles opérations doivent être définies spécifiquement dans l’interface et lesquelles dans les classes composites.
* Les **ajustements ultérieurs** des propriétés du composite (par exemple, la restriction des éléments enfants autorisés) s'avèrent également compliqués. 

Globalement, ce design pattern reste très utile et pratique , offrant plus d’avantages que d'inconvénients. 

### Exemple <a id="exempleComposite"></a>

Pour commencer, on crée l'interface qui sera implémentée par toutes les classes. Comme nous l'avons dis plus haut, Le **“Composant”** représente ici une interface qui définit les comportements / opérations commun(e)s de chaque composants (feuille et composite) dans l’arborescence. 
```java
public interface Forme {
    public void dessiner(String couleur);
}
```
Deuxièmement, on crée les différentes classes. Ces dernières réprésentes les feuilles implémentant la méthode permettant d'afficher la couleur de la forme choisie. 
```java
public class Carre implements Forme{

    @Override
    public void dessiner(String couleur) {

        System.out.println("Dessin du carre de la couleur " + couleur);
    }
}

public class Cercle implements Forme{

    @Override
    public void dessiner(String couleur) {
        System.out.println("Dessin du cercle de la couleur " + couleur);
    }
}
```
Pour finir, on s'interesse à la classe composite. C'est cette dernière qui représente la hiérarchie. Il comprends les feuilles précédemment implémentées : le carré et le cercle. On y ajoute aussi les méthodes d'ajout et de supression d'éléments. 
```java
public class Dessin implements Forme{

    private List<Forme> formes = new ArrayList<Forme>();

    @Override
    public void dessiner(String couleur) {
        for(Forme f : formes){
            f.dessiner(couleur);
        }
    }

    public void ajouter(Forme f){
        this.formes.add(f);
    }

    public void retirer(Forme f){
        this.formes.remove(f);
        System.out.println("On a retirer une forme du dessin");
    }
}
```
Voici un exemple d'utilisation de ce Composite. 
```java
public class  Main {
    public static void main(String[] args) {
        Forme carre= new Carre();
        Forme cercle= new Cercle();

        Dessin dessin = new Dessin();
        dessin.ajouter(carre);
        dessin.ajouter(cercle);

        dessin.dessiner("violet");

        dessin.retirer(carre);
    }
}
```
On obtient dans la console :
```
Dessin du carre de la couleur violet
Dessin du cercle de la couleur violet
On a retirer une forme du dessin
```





