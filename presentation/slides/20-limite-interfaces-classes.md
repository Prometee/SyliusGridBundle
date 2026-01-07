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

