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

SELECT `degrees`.`id`, `degrees`.`name`, `degrees`.`level`, `departments`.`id` as 'departments_id' , `departments`.`name` AS 'name_department'
FROM `departments`
JOIN `degrees` ON `departments`.`id` = `degrees`.`department_id`
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

SELECT `students`.`id`, `students`.`surname` AS 'Student_name', `students`.`name` AS 'Student_name' , `students`.`registration_number`, `degrees`.`name`
FROM `students`
JOIN `degrees` on `students`.`degree_id` = `degrees`.`id`
JOIN `departments` on `degrees`.`department_id` = `departments`.`id`
order BY `students`.`surname`, `students`.`name`

5. Selezionare tutti i corsi di laurea con i relativi corsi e insegnanti

# Selezionare tutti i corsi di laurea con i relativi corsi e insegnanti

#taachers
#courses
#degrees
SELECT `degrees`.`id`, `degrees`.`name`, `courses`.`id`, `courses`.`name`, `teachers`.`id`, `teachers`.`name`, `teachers`.`surname`
FROM `degrees`
JOIN `courses` on `degrees`.`id` = `courses`.`degree_id`
JOIN `course_teacher` on `courses`.`id` = `course_teacher`.`course_id`
JOIN `teachers` ON `course_teacher`.`teacher_id` = `teachers`.`id`

6. Selezionare tutti i docenti che insegnano nel Dipartimento di Matematica (54)
#teachers
#departments
#degrees

SELECT DISTINCT departments.name, teachers.id, teachers.name
FROM departments
JOIN `degrees` on `departments`.`id` = `degrees`.`department_id`
JOIN `courses` ON `degrees`.`id` = `courses`.`degree_id`
JOIN `course_teacher` on `courses`.`id` = `course_teacher`.`course_id`
JOIN `teachers` ON `course_teacher`.`teacher_id` = `teachers`.`id`

WHERE departments.name = 'Dipartimento di Matematica'


7. BONUS: Selezionare per ogni studente quanti tentativi d’esame ha sostenuto per superare ciascuno dei suoi esami
# 7. BONUS: Selezionare per ogni studente quanti tentativi d’esame ha sostenuto per superare ciascuno dei suoi esami
#exam_student
#students
# 7. BONUS: Selezionare per ogni studente quanti tentativi d’esame ha sostenuto per superare i suoi esami.
#exam_student
#students

SELECT  COUNT(exams.id) as 'numero_di_esami', students.id, `students`.`name`, `students`.`surname`
FROM exams
JOIN exam_student ON exams.id = exam_student.exam_id
left JOIN students ON exam_student.student_id = students.id
GROUP BY students.id 
ORDER BY `students`.`name`, `students`.`surname`
