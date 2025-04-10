## Modellizzare la struttura di un database per memorizzare tutti i dati riguardanti una università:
sono presenti diversi **Dipartimenti** (es.: Lettere e Filosofia, Matematica, Ingegneria ecc.);
ogni **Dipartimento** offre più **Corsi di Laurea** (es.: Civiltà e Letterature Classiche, Informatica, Ingegneria Elettronica ecc..)
ogni **Corso di Laurea** prevede diversi **Corsi** (es.: Letteratura Latina, Sistemi Operativi 1, Analisi Matematica 2 ecc.);
ogni **Corso** può essere tenuto da diversi **Insegnanti**;
ogni **Corso** prevede più **appelli d'Esame**;
ogni **Studente** è iscritto ad un solo **Corso di Laurea**;
ogni **Studente** può iscriversi a più **appelli di Esame**;
per ogni **appello d'Esame** a cui lo **Studente** ha partecipato, è necessario memorizzare il voto ottenuto, anche se non sufficiente. Pensiamo a quali entità (tabelle) creare per il nostro database e cerchiamo poi di stabilirne le relazioni. Infine, andiamo a definire le colonne e i tipi di dato di ogni tabella.

# University

## departement 
id: INT - PRIMARY KEY - AUTO_INCREMENT
Name: VARCHAR(255) - NOTNULL


## degre_program
id:	INT - PRIMARY KEY - AUTO_INCREMENT
departement_id: FOREIGN KEY - BIGINT - NOTNULL
name:	VARCHAR(50) - NOT NUL

## subjects
id:	INT - PRIMARY KEY - AUTO_INCREMENT
name:	VARCHAR(50)	NOT NULL
id_degree_program: FOREIGN KEY - BIGINT - NOTNULL

## teacher 
id:	INT - PRIMARY KEY - AUTO_INCREMENT
name:	VARCHAR(50)	NOT NUL
last_name: VARCHAR(50) NOT NULL,
email: VARCHAR(10) NOT NULL - UNIQUE

## subject_teacher
subject_id: FOREIGN KEY - BIGINT - NOTNULL
teacher_id: FOREIGN KEY - BIGINT - NOTNULL


## exams_sessions
id:	INT - PRIMARY KEY - AUTO_INCREMENT
subject_id: FOREIGN KEY - BIGINT - NOTNULL
date: DATE

## students
id:	INT - PRIMARY KEY - AUTO_INCREMENT
name:	VARCHAR(50) - NOTNUL
last_name:VARCHAR(50) NOT NULL,
student_number: VARCHAR(10) - NOTNULL - UNIQUE
degree_program_id: FOREIGN KEY - BIGINT - NOTNULL
year: YEAR

## exam_student
student_id: FOREIGN KEY - BIGINT - NOTNULL
exam_id: FOREIGN KEY - BIGINT - NOTNULL
vote: (TINYINT) NOTNULL