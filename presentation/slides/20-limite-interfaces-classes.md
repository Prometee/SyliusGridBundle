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

L'interface définit un type générique : array<string, mixed>. C'est correct pour l'interface car on ne sait pas à l'avance quelle sera la structure exacte.

Mais dans les classes finales, on connaît la structure précise du tableau. Par exemple, NumericRangeFilter attend un array avec les clés greaterThan et lessThan.

L'IA n'a pas pu deviner ces array-shapes spécifiques. C'est un travail qui nécessite une connaissance métier que seul le développeur possède.
-->

