## live esempio
SELECT `courses`.`id` as `courses_id`, `courses`.`name`, `degrees`.`name`
FROM `91_univers`.`courses`
JOIN `91_univers`.`degrees` ON `courses`.`degree_id` = `degrees`.`id`
WHERE `degrees`.`name` = 'Corso di laurea in informatica';

### Join Lorenzo 2:
Selezionare le informazioni sul corso con id = 144, con tutti i relativi appelli d’esame
select `courses`.`id` as `courses_id`, `courses`.`name`, `exams`.`id` as `exsam_id`, `courses`.`description`, `courses`.`year`, `courses`.`cfu`
FROM `courses`
JOIN `exams` on `courses`.`id` = `exams`.`course_id`
WHERE `course_id` = 144;

### CArmelo query joint 3:
Selezionare a quale dipartimento appartiene il Corso di Laurea in Diritto
dell'Economia (Dipartimento di Scienze politiche, giuridiche e studi internazionali)
sbagliata

SELECT * FROM `departments` JOIN `degrees` on `departments`.`id` = `degrees`.`department_id` WHERE `degrees`.`name` = "corso di laure in diritto";

## Rizzo Join 4:
Selezionare tutti gli appelli d'esame del Corso di Laurea Magistrale in Fisica del primo anno

SELECT `courses`.`name` as `name_courses`, `courses`.`period`, `courses`.`cfu`, `exams`.`date`, `exams`.`address`, `degrees`.`name` as 'degree_name'
FROM `degrees`
JOIN `courses` on `degrees`.`id` = `courses`.`degree_id`
JOIN `exams` on `courses`.`id` = `exams`.`course_id`
WHERE `degrees`.`name` = 'corso di laurea magistrale in fisica'
AND `courses`.`year` = 1;

### Join Giuseppe 5:

Selezionare tutti i docenti che insegnano nel Corso di Laurea in Lettere (21)

SELECT `teachers`.* 
FROM `teachers` 
JOIN `course_teacher` on `teachers`.`id` = `course_teacher`.`teacher_id`
JOIN `courses` on `course_teacher`.`course_id` = `courses`.`id`
JOIN `degrees` on `courses`.`degree_id` = `degrees`.`id`
WHERE `degrees`.`name` = 'Corso di Laurea in Lettere';

### Join Riccardo 6:

Selezionare il libretto universitario di Mirco Messina (matricola n. 620320)

SELECT `students`.`name` as 'student_name', `students`.`surname`, `students`.`registration_number`, `courses`.`id`, `courses`.`name`, `exam_student`.`vote`
FROM `exam_student`
JOIN `students` on `exam_student`.`student_id` = `students`.`id`
JOIN `exams` on `exam_student`.`exam_id` = `exams`.`id`
JOIN `courses` on `exams`.`course_id` = `courses`.`id`
WHERE `students`.`name` = 'Mirco'
AND `students`.`surname` = 'Messina'
AND `exam_student`.`vote` >= 18


### Roberto Nesta 7:

Selezionare il voto medio di superamento d'esame per ogni corso, con anche i dati
del corso di laurea associato, ordinati per media voto decrescente

#Selezionare il voto medio di superamento d'esame per ogni corso, con anche i dati
#del corso di laurea associato, ordinati per media voto decrescente
#exsam_student
#exsams
#courses
#degrees


SELECT AVG(`exam_student`.`vote`) AS 'media_voto', `courses`.`name` as 'course_name', `degrees`.`name` as 'degrees_name'
FROM `exam_student`
JOIN `exams` ON `exam_student`.`exam_id` = `exams`.`id`
JOIN `courses` ON `exams`.`course_id` = `courses`.`id`
JOIN `degrees` ON `courses`.`degree_id` = `degrees`.`id`
GROUP BY `courses`.`id`
ORDER BY `media_voto` DESC;
