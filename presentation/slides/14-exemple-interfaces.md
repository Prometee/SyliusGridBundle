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

