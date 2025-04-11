1. Selezionare tutti gli studenti nati nel 1990 (160)

SELECT *
FROM university_db.students
WHERE date_of_birth 
LIKE '1990%';

2. Selezionare tutti i corsi che valgono più di 10 crediti (479)

SELECT * 
FROM university_db.courses
WHERE cfu > '10';


3. Selezionare tutti gli studenti che hanno più di 30 anni

SELECT * 
FROM university_db.students
WHERE date_of_birth < '1995-04-10';


4. Selezionare tutti i corsi del primo semestre del primo anno di un qualsiasi corso di laurea (286)

SELECT * 
FROM university_db.courses
WHERE period = 'I semestre'
AND year = 1;


5. Selezionare tutti gli appelli d'esame che avvengono nel pomeriggio (dopo le 14) del 20/06/2020 (21)

SELECT * 
FROM university_db.exams
WHERE date = '2020-06-20'
AND hour > '14:00';


6. Selezionare tutti i corsi di laurea magistrale (38)

SELECT * 
FROM university_db.degrees
WHERE level = 'magistrale';


7. Da quanti dipartimenti è composta l'università? (12)

SELECT COUNT(*)
FROM university_db.departments;


8. Quanti sono gli insegnanti che non hanno un numero di telefono? (50)

SELECT COUNT(*)
FROM university_db.teachers
WHERE phone IS NULL


<!-- ........................................................................................ -->



1. Selezionare tutti gli studenti iscritti al Corso di Laurea in Economia

SELECT `students`.`id`, `students`.`name`, `students`.`surname`, `students`.`degree_id`, `degrees`.`name` as `name_degree`
FROM `students`
JOIN `degrees` ON `students`.`degree_id` = `degrees`.`id`
WHERE `degrees`.`name` = 'Corso di Laurea in Economia';


2. Selezionare tutti i Corsi di Laurea Magistrale del Dipartimento di Neuroscienze

SELECT `degrees`.*
FROM `degrees`
JOIN `departments` ON `degrees`.`department_id` = `departments`.`id`
WHERE `degrees`.`level` = 'Magistrale'
AND `departments`.name = 'Dipartimento di Neuroscienze'


3. Selezionare tutti i corsi in cui insegna Fulvio Amato (id=44)

SELECT `courses`.`id`, `courses`.`name`, `teachers`.`name`, `teachers`.`surname`, `teachers`.`id`
FROM `courses`
JOIN `course_teacher` ON `course_teacher`.`course_id` = `courses`.`id`
JOIN `teachers` ON `course_teacher`.`teacher_id` = `teachers`.`id`
WHERE `teachers`.`id` = '44'

4. Selezionare tutti gli studenti con i dati relativi al corso di laurea a cui sono iscritti e il relativo dipartimento, in ordine alfabetico per cognome e nome

SELECT `students`.`id`, `students`.`name`, `students`.`surname`, `degrees`.`name` AS `degree_name`, `departments`.`name` AS `department_name`
FROM `students`
JOIN `degrees` ON `students`.`degree_id` = `degrees`.`id`
JOIN `departments` ON `degrees`.`department_id` = `departments`.`id`
ORDER BY `students`.`surname` ASC 


5. Selezionare tutti i corsi di laurea con i relativi corsi e insegnanti
6. Selezionare tutti i docenti che insegnano nel Dipartimento di Matematica (54)
7. BONUS: Selezionare per ogni studente il numero di tentativi sostenuti per ogni esame, stampando anche il voto massimo. Successivamente, filtrare i tentativi con voto minimo 18.