---
marp: true
theme: default
paginate: true
style: |
  section {
    font-family: 'Inter', 'SF Pro Display', 'Segoe UI', sans-serif;
    background: linear-gradient(135deg, #0f0f1a 0%, #1a1a2e 50%, #16213e 100%);
    color: #e8e8e8;
    position: relative;
  }
  section > * {
    position: relative;
    z-index: 1;
  }
  section[data-marpit-pagination]::after {
    z-index: 2;
  }
  h1 {
    color: #00d4aa;
    font-weight: 700;
    text-shadow: 0 0 30px rgba(0, 212, 170, 0.3);
  }
  h2 {
    color: #64b5f6;
    font-weight: 600;
  }
  strong {
    color: #00d4aa;
  }
  a {
    color: #64b5f6;
  }
  code {
    background-color: rgba(255, 255, 255, 0.1);
    border-radius: 4px;
    padding: 2px 6px;
    color: #ffc66d;
  }
  li {
    margin-bottom: 0.3em;
  }
  /* Darcula theme (PhpStorm) */
  pre {
    background-color: #2b2b2b;
    border-radius: 8px;
    color: #a9b7c6;
  }
  pre code {
    background-color: transparent;
    color: #a9b7c6;
  }
  pre code .hljs-keyword {
    color: #cc7832;
  }
  pre code .hljs-type,
  pre code .hljs-built_in {
    color: #ffc66d;
  }
  pre code .hljs-string {
    color: #6a8759;
  }
  pre code .hljs-comment {
    color: #629755;
    font-style: italic;
  }
  pre code .hljs-comment .hljs-doctag {
    color: #629755 !important;
    font-style: italic;
    font-weight: bold;
  }
  pre code .hljs-phpdoc {
    color: #629755 !important;
    font-style: italic;
  }
  pre code .hljs-function,
  pre code .hljs-title {
    color: #ffc66d;
  }
  pre code .hljs-variable,
  pre code .hljs-params {
    color: #a9b7c6;
  }
  pre code .hljs-number {
    color: #6897bb;
  }
  pre code .hljs-class,
  pre code .hljs-title.class_ {
    color: #a9b7c6;
  }
  pre code .hljs-attr,
  pre code .hljs-property {
    color: #9876aa;
  }
  pre code .hljs-doctag {
    color: #629755;
    font-style: italic;
  }
  pre code .hljs-meta {
    color: #bbb529;
  }
  .columns {
    display: grid;
    grid-template-columns: 1fr 1fr;
    gap: 1rem;
  }
  .highlight {
    background: linear-gradient(120deg, #00d4aa 0%, #64b5f6 100%);
    padding: 0.2em 0.4em;
    border-radius: 4px;
    color: #0f0f1a;
  }
  section::after {
    color: rgba(255, 255, 255, 0.5);
  }
  .stat-box {
    background: rgba(255, 255, 255, 0.05);
    border-left: 4px solid #00d4aa;
    padding: 1rem;
    margin: 0.5rem 0;
  }
  table {
    background: transparent !important;
    border-collapse: collapse !important;
    width: auto !important;
  }
  th, td {
    background: rgba(43, 43, 43, 0.95) !important;
    color: #e8e8e8 !important;
    padding: 0.5rem 1rem !important;
    border: 1px solid #00d4aa !important;
  }
  th {
    background: #16213e !important;
    color: #ffffff !important;
    font-weight: 600 !important;
  }
  tr:nth-child(even) td {
    background: rgba(60, 60, 60, 0.95) !important;
  }
---


# Utiliser des agents IA pour corriger les erreurs PHPStan

## Retour d'expérience sur SyliusGridBundle

![bg right:40% 80%](https://sylius.com/wp-content/uploads/2021/03/sylius-logo-transparent-logo-and-letters.png)

**Meetup PHP Paris - 8 janvier 2026**
Believe - 24 Rue Toulouse Lautrec, 75017 Paris

<!--
Bonsoir à tous et bienvenue à ce meetup PHP Paris !

Ce soir, je vais vous partager mon retour d'expérience sur l'utilisation d'agents IA pour corriger des erreurs PHPStan
dans un projet open source : SyliusGridBundle.

On va voir ensemble comment j'ai réussi à réduire drastiquement la dette technique d'un bundle Symfony en collaborant
avec une IA.
-->


---

# 👋 Qui suis-je ?

## Francis HILAIRE

- 🎯 **Développeur Web Senior** chez HARMAN International
- 🎵 Marque **FLUX::** (solutions audio professionnelles)
- 🐘 Contributeur open source PHP/Symfony
- 🛒 **Key contributor** Sylius

![bg right:35% 90%](https://www.harman.com/sites/default/files/styles/crop_freeform/public/2022-06/HARMAN_Logo_Red_RGB.png)

<!--
Avant de commencer, laissez-moi me présenter rapidement.

Je suis Francis HILAIRE, développeur web senior chez HARMAN International, je m'occupe de toute l'IT de la marque FLUX::
qui développe des solutions audio professionnelles.

Je suis également contributeur open source dans l'écosystème PHP/Symfony, et notamment "Sylius Key contributor", le
framework e-commerce dont le bundle que nous allons voir ce soir est une partie intégrante.
-->


---

# 🎵 FLUX:: by HARMAN

- Depuis 2007, création d'outils logiciels audio intuitifs et innovants
- **Audio Immersif** (SPAT Revolution), **Analyse Audio** (MiRA), **Traitement Audio** (plugins)
- Utilisés en création musicale, live, post-production, mastering et installations sonores
- Stack technique du shop: **Symfony**, **Sylius**, **API Platform**

![bg opacity:0.25](https://www.flux.audio/wp-content/uploads/2019/05/Mac-SPAT-Freevox.png)

<!--
FLUX:: : c'est des logiciels audio pro depuis 2007.
Stack web de notre shop : Symfony + Sylius + API Platform.
-->


---

# 🛒 Qu'est-ce que Sylius ?

## Le framework e-commerce PHP moderne

- 🏗️ Basé sur **Symfony** (composants découplés)
- 📦 Architecture **modulaire** et extensible
- 🔌 API-first avec **API Platform**
- 🌍 Open source et communauté active
- 🎯 Conçu pour les projets e-commerce **sur mesure**

![bg opacity:0.25](https://images.unsplash.com/photo-1573665613043-b4a35da781ff?w=1920)

<!--
Pour ceux qui ne connaissent pas, Sylius est un framework e-commerce PHP moderne, basé sur Symfony.

Ce qui le distingue, c'est son architecture modulaire : chaque fonctionnalité est un bundle indépendant qu'on peut
utiliser séparément. Il est API-first grâce à API Platform, et conçu pour les projets e-commerce sur mesure plutôt que
pour du "out of the box".
-->


---

# 📊 SyliusGridBundle

## Créer des vues de listing puissantes

```php
#[AsGrid(name: 'app_book')]
final class BookGrid extends AbstractGrid
{
    public function buildGrid(GridBuilderInterface $builder): void
    {
        $builder
            ->addField(StringField::create('title'))
            ->addField(DateTimeField::create('createdAt'))
            ->addFilter(StringFilter::create('search', ['title', 'author']))
            ->addActionGroup(MainActionGroup::create(
                CreateAction::create(),
            ));
    }
}
```

<!--
Le bundle sur lequel j'ai travaillé s'appelle SyliusGridBundle. C'est un composant qui permet de créer des vues de
listing configurables.

Comme vous pouvez le voir dans cet exemple, on définit une grille avec:
- des champs
- des filtres
- et des actions

Le tout est déclaratif et très flexible.

C'est utilisé dans l'admin de Sylius pour afficher toutes les listes comme les produits, les commandes, les clients, etc.
-->


---

# 📊 SyliusGridBundle - Fonctionnalités

<div class="columns">
<div>

### Sources de données
- 🗄 Doctrine ORM/ODM ou DQL
- 💎 Classes PHP
- 🔍 Elasticsearch
- 🌐 API externes
- ♾️ N'importe quelle source de données

</div>
<div>

### Fonctionnalités
- 📋 Colonnes configurables
- 🔍 Filtres multiples
- ↕️ Tri dynamique
- 📄 Pagination
- ⚡ Actions (par ligne, globales, ou en masse)

</div>
</div>

<!--
Ce qui rend ce bundle puissant, c'est sa flexibilité au niveau des sources de données : Doctrine ORM, ODM, DQL,
mais aussi des classes PHP simples, Elasticsearch, ou même des API externes.

Côté fonctionnalités, on a tout ce qu'il faut : colonnes configurables, filtres multiples, tri dynamique, pagination,
et différents types d'actions.

C'est un bundle assez conséquent avec beaucoup de code... et donc beaucoup de dette technique potentielle.
-->


---

# 🔍 PHPStan - Analyse statique pour PHP

## Trouver les bugs avant l'exécution

- 🐛 Détecte les erreurs **sans exécuter** le code
- 📊 Analyse les **types** (paramètres, retours, propriétés)
- 🎚️ **11 niveaux** de rigueur (0 = permissif → 10 = strict)
- 📝 **Baseline** : fichier pour ignorer temporairement des erreurs existantes
- 🔌 Extensions pour Symfony, Doctrine, PHPUnit...

![bg right:30% 80%](https://phpstan.org/images/phpstan.svg)

<!--
Avant de parler du défi, laissez-moi expliquer rapidement ce qu'est PHPStan pour ceux qui ne connaissent pas.

PHPStan c'est un outil d'analyse statique pour PHP.

Il analyse votre code sans l'exécuter et détecte des bugs potentiels, par exemple :
- mauvais types de paramètres
- retours incorrects
- détection de valeurs null
- etc.

Il fonctionne avec 11 niveaux de rigueur : le niveau 0 étant le plus permissif, le niveau 10 est le plus strict.

Une fonctionnalité importante est la "baseline" : c'est un fichier qui liste les erreurs existantes qu'on choisit
d'ignorer temporairement.
C'est pratique quand on adopte PHPStan sur un projet legacy, mais ça peut devenir une dette technique si on n'y fait
pas attention.
-->


---

# 🎯 Le défi : Nettoyer la baseline PHPStan

## Situation initiale

- 📊 **156 erreurs** dans la baseline PHPStan
- 🔴 Erreurs ignorées depuis longtemps
- 📉 Dette technique accumulée
- 🎯 Objectif : réduire drastiquement ce nombre

![bg opacity:0.25](https://media.giphy.com/media/v1.Y2lkPTc5MGI3NjExcGY2ZWIwZDhwc20wOGZtaGJ3N3U1eW9nZTJwdHZicXZhNzlpa3dsZSZlcD12MV9naWZzX3NlYXJjaCZjdD1n/kspVl6FzbdblOMKRmM/giphy.gif)

<!--
Maintenant, parlons du défi concrètement.

SyliusGridBundle avait une baseline avec 156 erreurs ignorées.
Ces erreurs s'accumulaient depuis longtemps et représentaient une vraie dette technique.

Mon objectif : réduire drastiquement ce nombre. Mais corriger 156 erreurs manuellement, c'est fastidieux et chronophage.
C'est là que l'IA entre en jeu.
-->

---

# 🤖 L'approche : Agents IA

## Pourquoi utiliser un agent IA ?

- ⏱️ **Gain de temps** : analyse rapide du code
- 🔍 **Exhaustivité** : ne rate aucun fichier
- 📝 **Documentation** : génère des commits détaillés
- 🔄 **Itératif** : corrections progressives et vérifiables

<!--
Pourquoi j'ai choisi d'utiliser un agent IA pour ce travail ?

Premièrement, le gain de temps : l'IA peut analyser rapidement tout le code et identifier les patterns d'erreurs.

Deuxièmement, l'exhaustivité : contrairement à un humain qui peut oublier un fichier, l'IA parcourt systématiquement tout le projet.

Troisièmement, la documentation : l'IA génère des messages de commit détaillés qui expliquent chaque correction.

Et enfin, le processus est itératif : on peut corriger progressivement et vérifier à chaque étape.
-->


---

# 🛠️ L'outil : Augment Code

## Agent IA intégré à l'IDE

- 🔌 Extension PHPStorm / JetBrains / VS Code
- 🧠 **Moteur de contexte** : indexe et comprend toute la codebase
- 🤖 Modèles : Claude, GPT-4, etc.
- 🔧 Modifie les fichiers et exécute les commandes
- ✅ Produit du code prêt pour la production

<!--
Augment Code : extension JetBrains avec Claude.
Sa force : un moteur de contexte qui indexe et comprend toute la codebase pour produire du code prêt pour la production.
-->


---

# 📋 Méthodologie de travail

## Workflow collaboratif Humain + IA

1. **Tâche précise** : Guider l'IA sur un type d'erreur spécifique
2. **Fichiers Markdown** : Récapituler les tâches (mémoire limitée)
3. **Proposition** : L'IA suggère des corrections
4. **Revue** : Le développeur valide/ajuste
5. **Vérification** : PHPStan + Tests
6. **Itération** : Si erreur on itère
7. **Commit** : Message détaillé

<!--
Voici le workflow que j'ai suivi.

Point crucial : si vous ne savez pas ce que vous voulez faire, l'IA peut partir dans tous les sens et faire
n'importe quoi.
Par contre, si vous la guidez avec une tâche très précise, elle va s'y atteler et la faire correctement.

C'est pour ça que je procède par catégorie d'erreurs : d'abord l'IA analyse la baseline et identifie les erreurs
PHPStan par type.

Autre point important : les IA ont une mémoire limitée.
Je lui demande donc de créer des fichiers Markdown qui récapitulent les tâches à effectuer.
Ça facilite les retours en arrière, et surtout, si l'agent plante ou ne répond plus, ça permet de garder un contexte
sain pour reprendre le travail.

Ensuite, je lui demande de corriger un type précis. Elle propose des corrections, je revois chaque proposition, et on itère.

On vérifie que PHPStan passe et que les tests sont toujours verts.

Itération : si erreur on itère

Et enfin une fois validé, on commit avec un message détaillé. 

-->


---

# 📊 Exemple concret #1 : Types d'arguments

<div class="columns">
<div class="column">

**Avant 😰**
```php
/**
 * PAS DE PHPDOC
 */
public function apply(
    DataSourceInterface $dataSource,
    string $name,
    $data,
    array $options
): void
    
    ...
    
// Parameter #1 $data of method
// expects array, mixed given.
    $greaterThan = $this->getDataValue(
        $data,
        'greaterThan',
    );
```

</div>
<div class="column">

**Après ✅**
```php
/**
 * @param array<string> $data
 */
public function apply(
    DataSourceInterface $dataSource,
    string $name,
    $data,
    array $options
): void
    
    ...
    
    
    
    $greaterThan = $this->getDataValue(
        $data,
        'greaterThan',
    );
```

</div>
</div>

<!--
Premier cas : les erreurs de type d'arguments.
Cette méthode est dans une classe finale qui implémente une interface.
L'interface définit $data comme mixed, mais cette implémentation n'accepte que des array de string.

Il faut comprendre l'entièreté du contexte de la classe pour savoir si la correction via une PHPDoc est requise.
On ajoute un @param pour préciser le type sans modifier la signature de l'interface ni le fonctionnement de la classe.
-->


---

# 📊 Exemple concret #2 : Retours de méthodes

<div class="columns">
<div class="column">

**Avant 😰**
```php
/**
 * NO PHPDOC
 */
// Method has no return type specified.
private function getCurrentlySortedBy(): array
{
    return $this->parameters->has('sorting')
        ? array_merge(
            $this->definition->getSorting(),
// Parameter #2 $arrays expects array, mixed given.
            $this->parameters->get('sorting'),
          )
        : $this->definition->getSorting()
    ;
}
```

</div>
<div class="column">

**Après ✅**
```php
/**
 * @return array<string, string>
 */
private function getCurrentlySortedBy(): array
{
  $default = $this->definition->getSorting();
  if (!$this->parameters->has('sorting')) {
    return $default;
  }

  /** @var array<string, string> $sorting */
  $sorting = $this->parameters->get('sorting');
  return array_merge($default, $sorting);
}
```

</div>
</div>

<!--
Deuxième exemple : les retours de méthodes non typés.

Ici, on avait une méthode qui retournait un array sans préciser son contenu.
PHPStan ne pouvait pas vérifier que les appelants utilisaient correctement le retour.

L'IA a ajouté l'annotation @return avec le type précis, et a aussi refactoré le code pour le rendre plus lisible et mieux typé.

Notez qu'elle a aussi ajouté un @var inline sur la variable intermédiaire pour que PHPStan puisse suivre le type à travers l'`array_merge`.
-->


---

# 📊 Exemple concret #3 : Interfaces PHPDoc

<div class="columns">
<div class="column">

**Avant 😰**
```php
// Method has parameter $data
// with no type specified.
// Method has parameter $options
// with no value type in array.
public function render(
    Field $field,
    $data,
    array $options
): string;
```

</div>
<div class="column">

**Après ✅**
```php
/**
 * @param array<string, mixed> $options
 */
public function render(
    Field $field,
    mixed $data,
    array $options
): string;
```

</div>
</div>

L'IA a corrigé **toutes les implémentations** automatiquement.

<!--
Troisième exemple : les interfaces.

Quand on modifie une interface, il faut aussi modifier toutes ses implémentations.
Ici, on a ajouté le type mixed explicite sur le paramètre $data et une annotation PHPDoc pour le paramètre $options.

Petite parenthèse ici : l'ajout du mot-clé mixed sur le paramètre pourrait aussi être fait avec PHPStorm via
Refactor > Change Signature, qui propage automatiquement le changement aux implémentations.

Mais pour l'annotation PHPDoc, l'IA a automatiquement trouvé et mis à jour toutes les classes qui implémentent cette interface.
C'est exactement le genre de tâche répétitive où l'IA excelle et où un humain risque d'oublier un fichier.
-->


---

# 📈 Résultats : Commit majeur

## Fix argument.type PHPStan errors (60/61 fixed, 98.4%)

<div class="stat-box">

**16 fichiers modifiés** en un seul commit
- 84 insertions (+)
- 252 suppressions (-)

</div>

![bg opacity:0.25](https://media.giphy.com/media/3o7qDSOvfaCO9b3MlO/giphy.gif)

<!--
Voici un exemple de résultat concret : un seul commit qui corrige 60 erreurs sur 61 de type "argument.type".

16 fichiers modifiés, 84 lignes ajoutées, 252 supprimées. Le fait qu'on supprime plus qu'on ajoute montre qu'on a aussi simplifié du code en passant.

Ce genre de commit aurait pris des heures à faire manuellement. Avec l'IA, c'était une question de minutes.
-->


---

# 📈 Progression globale

## Réduction de la baseline PHPStan

| Étape | Erreurs | Réduction |
|-------|---------|-----------|
| Initial | 156 | - |
| Après interfaces | 106 | -32% |
| Après argument.type | 31 | -80% |
| Final | ~10 | -94% |

🎯 **De 156 à ~10 erreurs** grâce à la collaboration IA

<!--
Voici la progression globale du projet.

On est partis de 156 erreurs. Après avoir corrigé les interfaces, on était à 106, soit 32% de réduction.

Après les erreurs de typage d'arguments, on est descendus à 31, soit 80% de réduction par rapport au départ.

Et au final, on arrive à environ 10 erreurs restantes, soit une réduction de 94%.

Ces 10 erreurs restantes sont des cas complexes qui nécessitent une réflexion plus approfondie sur l'architecture.
-->


---

# 🔧 Types de corrections effectuées

## Catégories d'erreurs corrigées

1. **argument.type** : 61 → 1 (98.4% corrigé)
2. **return.type** : Annotations manquantes
3. **missingType.iterableValue** : Arrays non typés
4. **property.type** : Propriétés sans type
5. **method.childReturnType** : Héritage incorrect

<!--
Voici les principales catégories d'erreurs qu'on a corrigées.

Les erreurs "argument.type" étaient les plus nombreuses : 61 au départ, il n'en reste qu'une seule.

On a aussi corrigé les retours de méthodes non annotés, les arrays sans type précis, les propriétés sans type, et les problèmes d'héritage où une classe enfant avait un type de retour incompatible avec le parent.

Chaque catégorie a été traitée méthodiquement, une par une.
-->


---

# 💡 Bonnes pratiques

## Ce que l'IA m'a aidé à appliquer

- 📝 **@var inline** avant les variables mixed
- 🔄 **Extraire** les variables pour mieux les typer
- 📋 **array<string, mixed>** plutôt que array
- 🎯 **class-string<T>** pour les noms de classes
- 📄 **Fichiers Markdown** pour récapituler les tâches (mémoire limitée)
- ✅ Toujours **vérifier** les suggestions de l'IA

<!--
Au-delà des corrections, l'IA m'a aidé à appliquer systématiquement des bonnes pratiques.

L'utilisation de @var inline avant les variables de type mixed, l'extraction de variables pour mieux les typer,
l'utilisation de array<string, mixed> plutôt que simplement array.

Et surtout, le type class-string<T> pour les noms de classes, qui permet à PHPStan de vérifier qu'on instancie bien le bon type.

Une bonne pratique que j'ai adoptée : demander à l'IA de créer des fichiers Markdown pour récapituler les tâches.
Les IA ont une mémoire limitée, et si votre agent plante ou ne répond plus, ces fichiers permettent de garder un contexte sain et de reprendre facilement.

Mais attention : il faut toujours vérifier les suggestions de l'IA. Elle n'est pas infaillible.
-->


---

# ⚠️ Limites et précautions

## L'IA n'est pas parfaite

- 🔍 **Revue humaine obligatoire**
- 🧪 **Tests** après chaque modification
- 📖 Comprendre **pourquoi** la correction fonctionne
- 🔄 Parfois besoin de **plusieurs itérations**
- 🎯 L'IA peut proposer des solutions **trop complexes**

![bg right:30% 80%](https://media.giphy.com/media/MCZ39lz83o5lC/giphy.gif)

<!--
Parlons maintenant des limites. L'IA n'est pas parfaite, et il y a des précautions à prendre.

Le point le plus important : si vous ne savez pas précisément ce que vous voulez, l'IA peut faire n'importe quoi.
Elle a besoin d'instructions claires et d'une tâche bien définie.
Par contre, quand vous la guidez sur une tâche précise, elle s'y attelle et la fait correctement.
Cela implique de savoir ce que l'on fait.

La revue humaine reste obligatoire. On ne peut pas faire confiance aveuglément à l'IA.

Il faut lancer les tests après chaque modification pour s'assurer qu'on n'a rien cassé.

Il faut comprendre pourquoi la correction fonctionne, pas juste l'accepter.

Parfois, l'IA a besoin de plusieurs itérations pour trouver la bonne solution.
Et parfois, elle propose des solutions trop complexes qu'il faut simplifier.
-->


---

# ⚠️ Limite : Interfaces vs Classes finales

<div class="columns">
<div class="column">

**✅ FilterInterface.php**
```php
/**
 * @param array<string, mixed> $options
 */
public function apply(
    DataSourceInterface $dataSource,
    string $name,
    $data,
    array $options
): void;
```

</div>
<div class="column">

**❌ NumericRangeFilter.php**
```php
/**
 * PHPDoc manquante:
 * @param array{
 *     greaterThan?: string,
 *     lessThan?: string,
 * } $data
 */
public function apply(
    DataSourceInterface $dataSource,
    string $name,
    $data,
    array $options
): void;
```

</div>
</div>

**→ Array-shape des classes finales à compléter manuellement**

<!--
Voici une limite concrète que j'ai rencontrée.

L'interface définit un type générique : array<string, mixed>.
C'est correct pour l'interface, car on ne sait pas à l'avance quelle sera la structure exacte.

Dans cette classe finale, on connaît la structure précise du tableau.
Par exemple, NumericRangeFilter attend un array avec soit une clé greaterThan, soit une clé lessThan ou les deux,
et à laquelle on passe un string qui est une valeur numérique à filtrer.

L'IA n'a pas pu deviner ces array-shapes spécifiques.
C'est un travail qui nécessite une connaissance métier ici l'IA ne sait pas que ce filtre dépend d'un FormType qui va valider la donnée.
-->


---

# 🎓 Leçons apprises

## Retour d'expérience

1. ✅ L'IA excelle pour les **tâches répétitives**
2. ✅ Gain de temps **significatif** (heures → minutes)
3. ⚠️ Toujours **valider** les propositions
4. ⚠️ L'IA a besoin de **contexte** clair

![bg opacity:0.25](https://i.giphy.com/media/v1.Y2lkPTc5MGI3NjExcWRtOWRqOXBqMnBxdnBxbXBxbXBxbXBxbXBxbXBxbXBxbXBxbXBxbSZlcD12MV9pbnRlcm5hbF9naWZfYnlfaWQmY3Q9Zw/xT0xeJpnrWC4XWblEk/giphy.gif)

<!--
Quelles leçons j'ai tirées de cette expérience ?

L'IA excelle vraiment pour les tâches répétitives. Appliquer le même pattern de correction sur 50 fichiers, c'est exactement ce qu'elle fait de mieux.

Le gain de temps est significatif : ce qui aurait pris des heures se fait en minutes.

Mais il faut toujours valider les propositions. L'IA peut se tromper, surtout sur des cas marginaux.

L'IA a besoin d'un contexte clair et d'une tâche précise. Si vous lui demandez vaguement "corrige les erreurs PHPStan", elle risque de faire n'importe quoi.
Par contre, si vous lui dites "corrige les erreurs argument.type en ajoutant des annotations @param", elle va le faire méthodiquement et correctement.

Et n'oubliez pas : les IA ont une mémoire limitée.
Faites-leur créer des fichiers Markdown qui récapitulent les tâches.
Ça facilite les retours en arrière, et si l'agent plante, vous gardez un contexte sain pour reprendre.

C'est vraiment la clé : plus vous êtes précis et organisé, meilleurs sont les résultats.
-->


---

# 🚀 Autres contributions avec l'IA

## Au-delà de PHPStan

- 🔄 **Migration phpspec → PHPUnit**
- 📝 **Ajout d'attributs PHP 8** (AsGrid, AsFilter)
- 🧹 **Suppression de Psalm** (doublon avec PHPStan)
- 📦 **Refactoring** du GridBuilder
- 🔧 **Support Symfony 8**

<!--
Au-delà de PHPStan, j'ai utilisé l'IA pour d'autres contributions sur ce bundle.

La migration de phpspec vers PHPUnit : l'IA a converti tous les tests automatiquement.

L'ajout d'attributs PHP 8 comme AsGrid et AsFilter pour remplacer la configuration YAML.

La suppression de Psalm qui faisait doublon avec PHPStan.

Le refactoring du GridBuilder pour une API plus fluide.

Et le support de Symfony 8.
-->


---

# 🛠️ Outils complémentaires

## Stack d'analyse statique

- **PHPStan** : Analyse statique principale
- **phpstan-symfony** : Extension Symfony
- **phpstan-doctrine** : Extension Doctrine
- **ECS** : Easy Coding Standard
- **Rector** : Refactoring automatisé

<!--
Pour ceux qui veulent reproduire cette approche, voici la stack d'outils que j'utilise.

PHPStan comme outil d'analyse statique principal, avec les extensions:
- phpstan-symfony
- phpstan-doctrine
pour une meilleure compréhension du framework.

ECS (Easy Coding Standard) pour le formatage du code.

Et Rector pour le refactoring automatisé.
D'ailleurs, Rector et l'IA se complètent très bien : Rector pour les transformations mécaniques, l'IA pour les cas plus complexes.
-->


---

# 📊 Avant / Après - Résumé

<div class="columns">
<div>

### Avant 😰
- 156 erreurs baseline
- Code legacy non typé
- PHPDoc incomplets
- Psalm + PHPStan

</div>
<div>

### Après 🎉
- ~10 erreurs baseline
- Types explicites
- PHPDoc complets
- PHPStan uniquement

</div>
</div>

![bg right:25% 90%](https://i.giphy.com/media/v1.Y2lkPTc5MGI3NjExcWRtOWRqOXBqMnBxdnBxbXBxbXBxbXBxbXBxbXBxbXBxbXBxbXBxbSZlcD12MV9pbnRlcm5hbF9naWZfYnlfaWQmY3Q9Zw/3ohzdIuqJoo8QdKlnW/giphy.gif)

<!--
Voici le résumé avant/après.

Avant : 156 erreurs dans la baseline, du code legacy non typé, des PHPDoc incomplets, et deux outils d'analyse (Psalm et PHPStan) qui faisaient doublon.

Après : environ 10 erreurs restantes, des types explicites partout, des PHPDoc complets, et un seul outil d'analyse.

Le code est maintenant beaucoup plus maintenable et les futurs contributeurs auront une meilleure DX (expérience de développement).
-->


---

# 🔮 Perspectives futures

## L'IA dans le développement PHP

- 🚀 Productivité **déjà décuplée** aujourd'hui
- 🤖 Agents de plus en plus **autonomes**
- 🔧 Intégration **CI/CD** avec IA
- 📝 Génération de **tests** automatique
- 🔍 **Code review** assistée par IA

<!--
Pour conclure, parlons des perspectives futures.

Notre productivité est déjà décuplée grâce à ces outils. Ce que je vous ai montré ce soir en est la preuve : des heures de travail réduites à quelques minutes.

Les agents IA deviennent de plus en plus autonomes.
On peut imaginer des intégrations CI/CD où l'IA corrige automatiquement certains types d'erreurs.

La génération de tests automatique est déjà possible et va s'améliorer.

La code review assistée par IA est un domaine en pleine expansion.

On n'est qu'au début de cette révolution.
-->


---

# 💬 Questions ?

## Ressources

- 📦 **SyliusGridBundle** : github.com/Sylius/SyliusGridBundle
- 📚 **Documentation** : stack.sylius.com/grid
- 🤖 **Augment Code** : augmentcode.com
- 🐘 **PHPStan** : phpstan.org

![bg right:30% 80%](https://media.giphy.com/media/l5RPZ6WjMv0k0/giphy.gif)

<!--
Voilà, je suis maintenant disponible pour répondre à vos questions.

Vous trouverez ici les liens vers les ressources mentionnées : le repository GitHub de SyliusGridBundle, la documentation, Augment Code, et PHPStan.

N'hésitez pas à me poser des questions sur l'utilisation de l'IA, PHPStan, ou Sylius en général.
-->


---

# 🙏 Merci !

## Francis HILAIRE

- 🐙 GitHub : **@Prometee**
- 🏢 HARMAN International / **FLUX::**
- 🛒 **Sylius Key contributor**

![bg right:40% 80%](https://media.giphy.com/media/V1dH38rUl9yX7xU8nh/giphy.gif)

**Meetup PHP Paris - 8 janvier 2026**

<!--
Merci beaucoup pour votre attention !

Vous pouvez me retrouver sur GitHub sous le pseudo Prometee.

Bonne soirée à tous et à bientôt !
-->


