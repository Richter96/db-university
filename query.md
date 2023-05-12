
## 1. Selezionare tutti gli studenti nati nel 1990 (160)
SELECT `name` FROM `students` WHERE `date_of_birth` LIKE '1990-%';
(160)


2. Selezionare tutti i corsi che valgono più di 10 crediti (479)
SELECT * FROM `courses` WHERE `cfu` > 10;
(479)

3. Selezionare tutti gli studenti che hanno più di 30 anni
SELECT * FROM `students` WHERE `date_of_birth` <= $'1993-05-12' ORDER BY `date_of_birth` ASC;
(3549)
SELECT * FROM `students` WHERE DATE_FORMAT(FROM_DAYS(DATEDIFF(NOW(), date_of_birth)), '%Y') >= 30;


4. Selezionare tutti i corsi del primo semestre del primo anno di un qualsiasi corso di laurea (286)
SELECT * FROM `courses` WHERE `period` LIKE 'I semestre' AND `year` LIKE '1';
(286)


5. Selezionare tutti gli appelli d'esame che avvengono nel pomeriggio (dopo le 14) del
20/06/2020 (21)
SELECT * FROM `exams`  WHERE `hour` >= '14:%' AND `date` =  '2020-06-20';
(21)


6. Selezionare tutti iseledi laurea magistrale (38)
SELECT * FROM `degrees` WHERE `level` LIKE 'Magistrale';
(38)


7. Da quanti dipartimenti è composta l'università? (12)
SELECT COUNT(*) FROM `departments`;
(12)



8. Quanti sono gli insegnanti che non hanno un numero di telefono? (50)
SELECT * FROM `teachers` WHERE `phone` IS NULL;
(50)
