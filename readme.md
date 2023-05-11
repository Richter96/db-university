# database intro library
Modellizzare la struttura di un database per memorizzare tutti i dati riguardanti una università:
- sono presenti diversi Dipartimenti (es.: Lettere e Filosofia, Matematica, Ingegneria ecc.);
- ogni Dipartimento offre più Corsi di Laurea (es.: Civiltà e Letterature Classiche, Informatica, Ingegneria Elettronica ecc..)
- ogni Corso di Laurea prevede diversi Corsi (es.: Letteratura Latina, Sistemi Operativi 1, Analisi Matematica 2 ecc.);
- ogni Corso può essere tenuto da diversi Insegnanti;
- ogni Corso prevede più appelli d'Esame;
- ogni Studente è iscritto ad un solo Corso di Laurea;
- ogni Studente può iscriversi a più appelli di Esame;
- per ogni appello d'Esame a cui lo Studente ha partecipato, è necessario memorizzare il voto ottenuto, anche se non sufficiente.
Pensiamo a quali entità (tabelle) creare per il nostro database e cerchiamo poi di stabilirne le relazioni.
Infine, andiamo a definire le colonne e i tipi di dato di ogni tabella.
Utilizzare https://www.diagrams.net/ per la creazione dello schema.
Esportare quindi il diagramma in jpg e caricarlo nella repo. (modificato) 


## data Types:

- strings: [varchar(number), char(number), text, longtext]
- numbers: [tinyint, small/medium int, int, bigint]
- decimals: [float(i, d), duble(i,,d), decimal(i,d)]
- date: [datatime, date, year, time, timestamp]

## attributes:

- NULL/ NOTNULLL
- DEFOULT
- AUTO_INCREMENT
- UNIQUE

## entity:
- dipartimenti
- corsi_di_laurea
    - ?materie?
- insegnanti
- appelli_esame 
- studenti 


## table:
- dipartimento one_to_many corsi_di_laure
- corsi_di_laure many_to_many materie
- materie many_to_many insegnanti
- materie one_to_many appelli_esame
- studenti many_to_many appelli_esame(voto d'esame)
- studneti one_to_many corsi_di_laurea
- 




## relationships:








## Table name: books
## columns: 


