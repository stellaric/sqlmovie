
## Exercice 1 - Nom et année de naissance des artistes nés avant 1950

```sql
SELECT nom , annéeNaiss
FROM artiste 
WHERE annéeNaiss <= 1950 ; 
```


## Exercice 2 - Titre de tous les drames

```sql
SELECT *
FROM film
WHERE genre = "Drame" \G
```

## Exercice 3 - Quels rôles a joué Bruce Willis.

```sql
SELECT a.nom, a.prénom, f.titre, r.nomRôle
FROM role AS r
INNER JOIN artiste AS a ON a.idArtiste = r.idActeur
INNER JOIN film AS f ON f.idFilm = r.idFilm
WHERE a.nom = "Willis";

```

## Exercice 4 - Qui est le réalisateur de Memento.

```sql
SELECT nom ,prénom ,titre 
FROM film AS f
INNER JOIN artiste AS a ON a.idArtiste=f.idRéalisateur
WHERE titre="Memento"
\G
```

## Exercice 5 - Quelles sont les notes obtenues par le film Fargo

```sql
SELECT titre , note
FROM notation as n 
INNER JOIN film as f on n.idFilm=f.idFilm 
where titre="Fargo" ;  
```
## Exercice 6 - Qui a joué le rôle de Chewbacca?

```sql
SELECT  idActeur , nom, prénom,nomRôle
FROM role as r 
Inner Join artiste as a on r.idActeur= a .idArtiste
WHERE nomRôle="Chewbacca";
```

## Exercice 7 - Dans quels films Bruce Willis a-t-il joué le rôle de John McClane
?

```sql
SELECT 
FROM 
WHERE 
```

## Exercice 8 - Nom des acteurs de 'Sueurs froides'

```sql
SELECT 
FROM 
WHERE 
```
## Exercice 9 - Quelles sont les films notés par l'internaute Prénom 0 Nom0

```sql
SELECT 
FROM 
WHERE 
```
## Exercice 10 - Films dont le réalisateur est Tim Burton, et l’un des acteurs Johnny Depp

```sql
SELECT 
FROM 
WHERE 
```
