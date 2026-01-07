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

PHPStan est un outil d'analyse statique pour PHP. Il analyse votre code sans l'exécuter et détecte des bugs potentiels : mauvais types de paramètres, retours incorrects, appels de méthodes sur null, etc.

Il fonctionne avec 11 niveaux de rigueur : le niveau 0 est très permissif, le niveau 10 est le plus strict.

Une fonctionnalité importante est la "baseline" : c'est un fichier qui liste les erreurs existantes qu'on choisit d'ignorer temporairement. C'est pratique quand on adopte PHPStan sur un projet legacy, mais ça peut devenir une dette technique si on n'y fait pas attention.
-->

