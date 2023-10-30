
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
SELECT titre , nomRôle , nom , prénom
FROM  film as f  
Inner Join role as r on r.idFilm =f.idFilm
Inner Join artiste as a on r.idActeur= a .idArtiste
WHERE nom="Willis" 
AND prénom="Bruce";
```

## Exercice 8 - Nom des acteurs de 'Sueurs froides'

```sql



```
## Exercice 9 - Quelles sont les films notés par l'internaute Prénom 0 Nom0

```sql
SELECT titre 
FROM film as f 
INNER JOIN notation as n ON f.idFilm=n.idFilm
INNER JOIN  internaute as i on n.email=i.email
WHERE i.nom="Nom0"
AND i.prénom="Prénom0";
```
## Exercice 10 - Films dont le réalisateur est Tim Burton, et l’un des acteurs Johnny Depp

```sql

```
## Exercice 11 - Titre des films dans lesquels a joué ́Woody Allen. Donner aussi le rôle.

```sql
SELECT 
FROM 
WHERE 
```
## Exercice 12 - Quel metteur en scène a tourné dans ses propres films ? Donner le nom, le rôle et le titre des films.

```sql
SELECT nom ,nomRôle , titre
FROM 
WHERE 
```
## Exercice 13 - 

```sql
SELECT 
FROM 
WHERE 
```
## Exercice 14 - Quel metteur en scène a tourné ́en tant qu’acteur ? Donner le  nom, le rôle et le titre des films dans lesquels cet artiste a joué.
 

```sql
SELECT nomRôle, nom, prénom, titre
FROM role as r 
INNER JOIN artiste as a  ON a.idArtiste = r.idActeur
INNER JOIN film as f ON f.idFilm = r.idFilm
WHERE idArtiste = f.idRéalisateur;

```
## Exercice 15 - Donnez les films de Hitchcock sans James Stewart 

```sql
SELECT 
FROM 
WHERE 
```
## Exercice 16 - Dans quels films le réalisateur a-t-il le même prénom que l’un des interprètes ? (titre, nom du réalisateur, nom de l’interprète). Le réalisateur et l’interprète ne doivent pas être la même personne.

```sql
SELECT 
FROM 
WHERE 
```
## Exercice 17 - Les films sans rôle

```sql
SELECT titre
FROM film
INNER JOIN role ON role.idFilm = film.idFilm
WHERE role.idActeur IS NULL;


```
## Exercice 18 - Quelles sont les films non notés par l'internaute Prénom1 Nom1

```sql
SELECT 
FROM 
WHERE 
```
## Exercice 19 - Quels acteurs n’ont jamais réalisé de film ?

```sql
SELECT idArtiste, nom,prénom 
FROM artiste 
WHERE idArtiste NOT IN(SELECT idActeur FROM role)  ;

```
## Exercice 20 - Quelle est la moyenne des notes de Memento

```sql
select * 
from notemoyenne
 where titre="Memento";
```
## Exercice 21 - id, nom et prénom des réalisateurs, et nombre de films qu’ils ont tournés.

```sql
SELECT  idArtiste ,nom,prénom , COUNT(*) as "Total film"
FROM artiste as a 
INNER JOIN film as f  on f.idRéalisateur=a.idArtiste
GROUP BY idArtiste,nom,prénom ;

```

## Exercice 22 - Nom et prénom des réalisateurs qui ont tourné au moins deux films

```sql
SELECT nom , prénom 
FROM artiste as a 
INNER JOIN film as f  on f.idRéalisateur=a.idArtiste
GROUP BY idArtiste
HAVING COUNT(*) =2;
```
## Exercice 23 - Quels films ont une moyenne des notes supérieure à 7

```sql
SELECT *
FROM notemoyenne
WHERE moyenne > 7 ;
```
