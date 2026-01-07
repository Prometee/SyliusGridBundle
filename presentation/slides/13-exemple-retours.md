# 📊 Exemple concret #2 : Retours de méthodes

<div class="columns">
<div class="column">

**Avant 😰**
```php
/**
 * NO PHPDOC
 */
private function getCurrentlySortedBy(): array
{
    return $this->parameters->has('sorting')
        ? array_merge(
            $this->definition->getSorting(),
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

Ici, on avait une méthode qui retournait un array sans préciser son contenu. PHPStan ne pouvait pas vérifier que les appelants utilisaient correctement le retour.

L'IA a ajouté l'annotation @return avec le type précis, et a aussi refactoré le code pour le rendre plus lisible et mieux typé.

Notez qu'elle a aussi ajouté un @var inline sur la variable intermédiaire pour que PHPStan puisse suivre le type à travers le array_merge.
-->

