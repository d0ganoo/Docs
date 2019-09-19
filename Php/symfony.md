
# Glossaire

## namespace

Les namespaces représentent un moyen d'encapsuler des éléments. Cela peut être conçu comme un concept abstrait, pour plusieurs raisons. 
Par exemple, dans un système de fichiers, les dossiers représentent un groupe de fichiers associés et servent d'espace de noms pour les fichiers qu'ils contiennent.
Un exemple concret est que le fichier foo.txt peut exister dans les deux dossiers /home/greg et /home/other, mais que les deux copies de foo.txt ne peuvent pas co-exister dans le même dossier. De plus, pour accéder au fichier foo.txt depuis l'extérieur du dossier /home/greg, il faut préciser le nom du dossier en utilisant un séparateur de dossier, tel que /home/greg/foo.txt. Le même principe s'applique aux espaces de noms dans le monde de la programmation.

## Interface

## Class

## Class abstraite

## Trait

## Visibilité des variables

```php
public $public = 'Public'; // Disponible partout
protected $protected = 'Protected'; // Disponibilité limité à la classe elle-même, ainsi qu'aux classes qui en héritent et parente
private $private = 'Private'; // Disponible uniquement dans la class qui les a définis
```
