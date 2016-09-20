# EA vers relationnel

## I. E/A cas simple

| EE | Table |
|---|---|
| Attribut | Attribute |
| Clé | Primary Key |
| Association | Dépend de la cardinalité : |
| | Table si (*, n) - (*, n) |
| | Si (1, 1) : ajouter les attributs PK de l'autre EE dans la table |
| | SI (0, 1) : à discuter |

## II. EE Faible

Idem + rajouter à la table tous les attributs clé.

Attribut support : ne se traduit par aucune table ou attribut supplémentaire.

## III. Sous entités

3 méthodes de traduction :

- Méthode des NULL
- Méthode OO
- Méthode Ensemble d'Entités

Différences :
- Espace disque
- Facitlité/Efficacité d'exécution des requêtes
