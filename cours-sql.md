# Cross join

C'est une jointure entre deux tables, un produit cartésien.

select ....
```sql
From emp join DEPT on EMP.lDID = DEPT.DID
	where SAL > 10000;
```

select ....
```sql
from EMP natural join DEPT WHERE SAL > 10000;
```

La différence entre le natural join et le cross join c'est que
le natural join est automatique (si il y à deux colonnes du même nom
dans les tables, il va faire la jointure)

Donc, les requêtes
`select *  from EMP natural join DEPT;`
et
`select *  from EMP, DEPT where EMP.DID = DEPT.DID;`
Sont équivalentes

**Ces jointures sont appellées des jointures internes**


