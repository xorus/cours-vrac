# Cross join

C'est une jointure entre deux tables, un produit cartésien.

```sql
select ....
From emp join DEPT on EMP.lDID = DEPT.DID
	where SAL > 10000;
```

```sql
select ....
from EMP natural join DEPT WHERE SAL > 10000;
```

La différence entre le natural join et le cross join c'est que
le natural join est automatique (si il y à deux colonnes du même nom
dans les tables, il va faire la jointure).

Et par rapport à un JOIN, on à pas besoin d'utiliser la clause ON.

Donc, les requêtes
`select *  from EMP natural join DEPT;`
et
`select *  from EMP, DEPT where EMP.DID = DEPT.DID;`
Sont équivalentes

**Ces jointures sont appellées des jointures internes**

Dans une jointure externe (OUTER JOIN), on retrouve aussi les tuples orphelins.

Par exemple :

| emp did | dept DID |
|---|---|
| Smith 3 | SALES 3 |
| James NULL | NULL NULL |
| NULL NULL | 4 OPERATION |

On obtient ces valeurs nulles dans le résultat de la requête car la jointure
met des null quand elle ne peut pas trouver le tuple cible.
Ici, le EMP.DID de James était NULL, sql joint donc des NULL. Dans une jointure interne, les lignes avec des NULL ne seraient pas dans le résultat.


## Tableau jointure d'état / jointure naturelle

| | theta | naturel |
|---|---|---|
|inner|T join S1 ON ... | T natural join S1 |
|outer|T outer join S1 ON...| T natural outer join S1 |

# Sous-requêtes

1. a.
```sql
select ...
from (sous req) as temp
where ...
```

b. La sous requête produit un scalaire sur lequel on peut comparer.
```sql
select ...
from ...
where SAL >= (
    select MAX(SAL)
    from EMP
    where ...
)
```

c. Utiliser une sous requête qui produit une liste, on veut vérifier si un tuple est dedans.
```sql
select ...
from EMP
where SAL IN (
    select SAL
    from EMP
    where ...
)
```
Par exemple pour sélectionner le salaire un employé dont le salaire est inférieur à tous les salaires des managers :
Le mot clé ALL retourne vrai si la condition marche pour tous les élements d'une liste.
```sql
select ...
from EMP
where SAL <= all (
    select SAL
    from EMP
    where JOB = 'MANAGER'
)
```
Il existe aussi le mot clé `ANY` ou `SOME` (synonymes). Comme son nom l'indique, il retournera vrai si AU MOINS un des éléments matche.




