# 📊 Exemple concret #1 : Types d'arguments

<div class="columns">
<div class="column">

**Avant 😰**
```php
// Erreur: mixed passé à une méthode typée
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
Passons aux exemples concrets. Premier cas : les erreurs de type d'arguments.

Ici, on avait une variable $data de type mixed qui était passée à une méthode getDataValue attendant un array typé.

La solution : ajouter une annotation @param sur la méthode pour préciser le type attendu de $data. Ainsi, PHPStan sait que $data est un array<string> et peut vérifier que l'appel à getDataValue est correct.

C'est une technique classique mais fastidieuse à appliquer manuellement sur des dizaines de fichiers. L'IA a identifié et corrigé ce pattern partout dans le code.
-->

