## 1. Selezionare tutti gli studenti iscritti al Corso di Laurea in Economia (68)

### studenti
### degrees

SELECT `students`.`name`, `students`.`surname`, `students`.`registration_number`, `degrees`.`name` AS 'name_degree'
FROM `students`
JOIN `degrees` on `students`.`degree_id` = `degrees`.`id`
WHERE `degrees`.`name` = 'Corso di Laurea in Economia';


2. Selezionare tutti i Corsi di Laurea Magistrale del Dipartimento di Neuroscienze

# 2. Selezionare tutti i Corsi di Laurea Magistrale del Dipartimento di Neuroscienze

### departments
### degrees

SELECT `degrees`.`id`, `degrees`.`name`, `degrees`.`level`, `departments`.`id` as 'departments_id' , `departments`.`name` AS 'name_department', `courses`.`name` AS 'course_name' 
FROM `departments`
JOIN `degrees` ON `departments`.`id` = `degrees`.`department_id`
JOIN `courses` ON `degrees`.`id` = `courses`.`degree_id`
WHERE `departments`.`name` = 'Dipartimento di Neuroscienze'
AND `degrees`.`level` = 'Magistrale';



3. Selezionare tutti i corsi in cui insegna Fulvio Amato (id=44)
## teachers
## course_teacher
## courses

SELECT `courses`.`id` as 'Courses_id', `courses`.`name` AS 'Corses_name', `teachers`.`id`, `teachers`.`name` AS 'Teacher_name', `teachers`.`surname` AS 'Corses_surname'
FROM `teachers`
JOIN `course_teacher` ON `teachers`.`id` = `course_teacher`.`teacher_id`
JOIN `courses` on `course_teacher`.`course_id` = `courses`.`id`
WHERE `teachers`.`name` = 'Fulvio'
AND `teachers`.`surname` = 'Amato';


4. Selezionare tutti gli studenti con i dati relativi al corso di laurea a cui sono iscritti e il relativo dipartimento, in ordine alfabetico per cognome e nome 
(non completa)

## students
## degrees
## departments

SELECT `students`.`id`, `students`.`name` AS 'Student_name' , `students`.`surname` AS 'Student_name', `students`.`registration_number`, `degrees`.`name`
FROM `students`
JOIN `degrees` on `students`.`degree_id` = `degrees`.`id`
JOIN `departments` on `degrees`.`department_id` = `departments`.`id`;


5. Selezionare tutti i corsi di laurea con i relativi corsi e insegnanti
6. Selezionare tutti i docenti che insegnano nel Dipartimento di Matematica (54)
7. BONUS: Selezionare per ogni studente quanti tentativi d’esame ha sostenuto per superare ciascuno dei suoi esami