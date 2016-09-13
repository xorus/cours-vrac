# Aggrégations et GROUP BY

## Fonctions d'aggrégation

Les fonctions d'aggrégation font des calculs verticaux : ils prennent le nom de la colonne et font une statistique sur celle-ci.

On retrouve les fonctions :

- `SUM()`
- `MIN()`
- `MAX()`
- `AVERAGE()`
- `COUNT()`

Utilisation par exemple :

```sql
select MAX(SAL)
from EMP
```

Retournera le salaire maximal pour tous les employé.

**Si il y a des NULLs**, ils sont ignorés.

## Regroupements avec `GROUP BY`

Un exemple de l'opérateur de regroupement :

```sql
select JOB, MAX(SAL)
from EMP
group by JOB
```

Il regroupera les tuples dans EMP qui ont une valeur de JOB identique.

C'est donc un regrouppement de tuples qui ont la même valeur.

Si on à :

| job | sal |
|-----|-----|
| AAA | |
| AAA | |
| BBB | |
| CCC | |
| CCC | |
| CCC | |
| CCC | |

Donnera en sortie

| job | sal |
|-----|-----|
| AAA | |
| BBB | |
| CCC | |

Un regroupement ne marche que si c'est logique, on ne pourra pas faire

**Ne fonctionnera pas:**

```sql
select JOB, MAX(SAL), ENAME
from EMP
group by JOB
```

CAR on peut retrouver des Noms d'employés différents dans la table.

Le problème logique qui se pose, c'est comment peut on regrouper par JOB et sortir un nom d'employé en même temps alors que l'on parle d'un regrouppement par JOB ?

----

L'ordre des valeurs dans la clause `group by` ne change rien :

```sql
group by A, B
# et
group by B, A
```

Produiront les mêmes résultats.

## clause `HAVING`

Having permet de donner une condition de groupage.

```sql
select JOB, MAX(SAL)
from EMP
group by JOB
having <condition>

```

La condition HAVING s'applique sur la colonne. Par exmple, condition peut être :
```sql
HAVING MAX(SAL) > x
```

Cette condition signifie : garder les groupes dont le MAX(SAL) est plus grand que x.

# Ordre de la requête

```sql
select
from
[ where     ]  -- optionnel
[ group by     -- optionnel
  [ having ]]  -- optionnel
[ order by  ]  -- optionnel
```


