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

