
1. Ispišite ime, prezime, patronus svih likova koji imaju patronusa i on je poznat.-

SELECT fname, lname, patronus

FROM hogwarts\_characters.characters

WHERE patronus IS NOT NULL AND patronus != 'Unknown';

1. Ispišite prezime likova čije prezime završava slovom 'e',

SELECT lname

FROM characters

WHERE lname LIKE 'e%’;

1. Izračunajte ukupne godine svih likova i ispišite to na ekran.

SELECT SUM(age) AS ukupne\_godine

FROM hogwarts\_characters;

ukupne\_godine // 247;

1. Ispišite ime, prezime i godine likova po opadajućem redosledu njihovih godina.

SELECT fname, lname, age

FROM hogwarts\_characters.characters

WHERE age IS NOT NULL

ORDER BY age DESC;

1. Ispišite ime likova i godine onih čije godine su u rasponu od 50 do 100 godina.

SELECT fname, age

FROM hogwarts\_characters.characters

WHERE age BETWEEN 50 AND 100;

1. Ispišite godine svih likova tako da među njima nema onih sa istim godinama.

SELECT DISTINCT age

FROM hogwarts\_characters.characters

WHERE age IS NOT NULL

ORDER BY age;

1. Ispišite sve informacije o likovima čiji je faculty = Gryffindor i čije su godine preko 30.

SELECT \*

FROM hogwarts\_characters.characters

WHERE faculty= 'Gryffindor' AND age > 30 ;

1. Ispišite imena prva tri fakulteta iz tabele tako da se fakulteti ne ponavljaju.

SELECT DISTINCT faculty

FROM hogwarts\_characters.characters

WHERE faculty IS NOT NULL

LIMIT 3;

1. Ispišite imena likova čije ime počinje sa 'N' i ima 5 slova, ili čije ime počinje sa 'L'.

SELECT fname

FROM characters

WHERE ( fname LIKE 'N\_\_\_\_’' OR fname LIKE 'L%');

1. Izračunajte prosečne godine svih likova.

SELECT AVG(age) AS avgage

FROM hogwarts\_characters.character

WHERE age IS NOT NULL;

1. Obrišite lika sa ID = 11.

DELETE FROM hogwarts\_characters.characters

WHERE char\_id = 11;

1. Ispišite prezime svih likova koja sadrže slovo 'a'.

SELECT lname

FROM hogwarts\_characters.characters

WHERE lname LIKE '%a%';

1. Koristite pseudonim da privremeno zamenite naziv kolone fname u Half-Blood Prince za stvarnog princa-polukrvnog.

SELECT fname AS "Half-Blood Prince", lname

FROM hogwarts\_characters.characters

WHERE fname = 'Severus' AND lname = 'Snape';

1. Ispišite id i imena svih patronusa po abecednom redu, pod uslovom da su poznati.

SELECT char\_id, patronus

FROM hogwarts\_characters.characters

WHERE patronus IS NOT NULL

ORDER BY patronus ASC;

1. Koristite operator IN, ispišite ime i prezime likova čije je prezime Crabbe, Granger ili Diggory.

SELECT fname, lname

FROM hogwarts\_characters.characters

WHERE lname IN ('Crabbe', 'Granger', 'Diggory');

1. Ispišite minimalne godine likova.

SELECT min(age)

FROM hogwarts\_characters.characters;

1. Koristite operator UNION, ispišite imena iz tabele characters i naslove knjiga iz tabele library.

SELECT fname AS name

FROM hogwarts\_characters.characters

UNION ALL

SELECT book\_name AS book

FROM hogwarts\_characters.library;

1. Koristite operator HAVING, izračunajte broj likova po svakom fakultetu, ostavljajući samo one fakultete gde je broj studenata veći od 1.

SELECT faculty, COUNT(\*) AS broj

FROM hogwarts\_characters.characters

GROUP BY faculty

HAVING COUNT(\*) > 1;
