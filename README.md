
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

## Exercice 7 - Dans quels films Bruce Willis a-t-il joué le rôle de John McClane ?

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
SELECT nom, prénom
FROM artiste
JOIN film ON artiste.idArtiste = film.idRéalisateur
WHERE film.titre = 'Sueurs froides';

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
SELECT titre
FROM role
JOIN artiste ON role.idActeur = artiste.idArtiste
JOIN film ON film.idFilm = role.idFilm
WHERE artiste.nom = 'Depp'
AND artiste.prénom = 'Johnny'
AND film.titre IN (
    SELECT titre
    FROM film
    JOIN artiste ON film.idRéalisateur = artiste.idArtiste
    WHERE artiste.nom = 'Burton'
    AND artiste.prénom = 'Tim'
);

```
## Exercice 11 - Titre des films dans lesquels a joué ́Woody Allen. Donner aussi le rôle.

```sql
SELECT titre, nomRôle
FROM film
JOIN role ON film.idFilm = role.idFilm
JOIN artiste ON artiste.idArtiste = role.idActeur
WHERE artiste.nom = 'Allen'
AND artiste.prénom = 'Woody';

```
## Exercice 12 - Quel metteur en scène a tourné dans ses propres films ? Donner le nom, le rôle et le titre des films.

```sql
SELECT a.nom, a.prénom, r.nomRôle, f.titre
FROM artiste a
JOIN role r ON a.idArtiste = r.idActeur
JOIN film f ON r.idFilm = f.idFilm AND f.idRéalisateur = a.idArtiste
WHERE f.idRéalisateur = a.idArtiste;

```
## Exercice 13 - Titre des films de Quentin Tarantino dans lesquels il n’a pas joué

```sql
SELECT titre
FROM film
WHERE idRéalisateur = (
    SELECT idArtiste
    FROM artiste
    WHERE nom = 'Tarantino' AND prénom = 'Quentin'
)
AND idFilm NOT IN (
    SELECT idFilm
    FROM role
    WHERE idActeur = (
        SELECT idArtiste
        FROM artiste
        WHERE nom = 'Tarantino' AND prénom = 'Quentin'
    )
);

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
SELECT f.titre 
FROM film f
JOIN artiste a1 ON f.idRéalisateur = a1.idArtiste AND a1.nom = 'Hitchcock'
LEFT JOIN role r ON f.idFilm = r.idFilm
LEFT JOIN artiste a2 ON r.idActeur = a2.idArtiste AND a2.nom = 'Stewart' AND a2.prénom = 'James'
WHERE a2.nom IS NULL;

```
## Exercice 16 - Dans quels films le réalisateur a-t-il le même prénom que l’un des interprètes ? (titre, nom du réalisateur, nom de l’interprète). Le réalisateur et l’interprète ne doivent pas être la même personne.

```sql
SELECT f.titre, r1.nom AS nomRéalisateur, r2.nom AS nomInterprète
FROM film f
JOIN artiste r1 ON f.idRéalisateur = r1.idArtiste
JOIN role ro ON f.idFilm = ro.idFilm AND r1.prénom = r2.prénom
JOIN artiste r2 ON ro.idActeur = r2.idArtiste AND r1.idArtiste != r2.idArtiste;

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
SELECT f.titre
FROM film f
LEFT JOIN notation n ON f.idFilm = n.idFilm
LEFT JOIN internaute i ON n.idInternaute = i.idInternaute
WHERE i.prénom = 'Prénom1' AND i.nom = 'Nom1'
   OR n.idFilm IS NULL;

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
