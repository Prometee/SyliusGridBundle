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

