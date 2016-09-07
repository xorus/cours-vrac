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
|--|--|
| Smith 3 | SALES 3 |
| James NULL | NULL NULL |
| NULL NULL | 4 OPERATION |

On obtient ces valeurs nulles dans le résultat de la requête car la jointure
met des null quand elle ne peut pas trouver le tuple cible.
Ici, le EMP.DID de James était NULL, sql joint donc des NULL. Dans une jointure interne, les lignes avec des NULL ne seraient pas dans le résultat.


## Tableau jointure d'état / jointure naturelle

| | theta | naturel |
|--|--|--|
|inner|T join S1 ON ... | T natural join S1 |
|outer|T outer join S1 ON...| T natural outer join S1 |


