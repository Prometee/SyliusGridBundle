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

