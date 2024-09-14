# SQL_Project_14-09-24
Projekt v rámci studia SDA - Python


Akademický systém správy kurzů

Tento projekt představuje návrh a implementaci databázové vrstvy pro aplikaci, která slouží k administrativní správě akademického systému. Aplikace umožňuje správu studentů, trenérů, kurzů a zápisů studentů na kurzy. Databáze byla navržena pomocí SQL a obsahuje tabulky pro ukládání informací o studentech, kurzech a trenérech, včetně pohledů (views) pro různé reporty.

 Struktura projektu

Projekt obsahuje následující složky:

- DDL – obsahuje definice databázových tabulek a pohledů.
- Tables/ – SQL soubory pro definici tabulek.
- Views/ – SQL soubory pro definici pohledů.
- Queries – SQL dotazy, které provádějí různé operace s daty.
- README.md – tento soubor, který popisuje projekt.

Struktura databáze

Databáze obsahuje následující tabulky:

1. Student:
   - „student_id“ (PK) – jedinečný identifikátor studenta.
   - „jmeno“ – jméno studenta.
   - „prijmeni" – příjmení studenta.
   - „datum_narozeni“ – datum narození studenta.

2. Trainer:
   - „trainer_id“ (PK) – jedinečný identifikátor trenéra.
   - „jmeno“ – jméno trenéra.
   - „prijmeni“ – příjmení trenéra.

3. Course:
   - „course_id“ (PK) – jedinečný identifikátor kurzu.
   - „nazev_kurzu“ – název kurzu.
   - „kredit“ – počet kreditů za kurz.
   - „trainer_id“ (FK) – odkaz na trenéra, který kurz vyučuje.

4. Student_Course_Signup:
   - „signup_id“ (PK) – jedinečný identifikátor zápisu.
   - „student_id“ (FK) – odkaz na studenta, který je zapsán na kurz.
   - „course_id“ (FK) – odkaz na kurz, na který je student zapsán.

Pohledy (Views)

V projektu byly vytvořeny následující pohledy:

1. courses_with_most_signed_up_students:
   - Tento pohled vrací TOP 5 kurzů s největším počtem zapsaných studentů.

2. report_all_data:
   - Zobrazuje všechny studenty, kurzy, a trenéry, propojené pomocí JOIN operací.

3. trainers_teaching_atleast_2_courses:
   - Vrací trenéry, kteří vyučují alespoň 2 kurzy.

4. trainers_with_highest_student_outreach:
   - Vrací TOP 3 trenéry, kteří mají nejvíce studentů zapsaných v jejich kurzech.

Jak projekt spustit

Krok 1: Vytvořte databázi v MySQL nebo jiném kompatibilním SQL nástroji.

Krok 2: Spusťte SQL skripty obsažené ve složce **DDL/Tables/**, abyste vytvořili tabulky.

Krok 3: Naplňte tabulky vzorovými daty pomocí skriptu **data_load.sql**.

Krok 4: Spusťte SQL skripty ve složce **DDL/Views/**, abyste vytvořili pohledy.

Krok 5: Použijte SQL dotazy ve složce **Queries/** pro testování a zobrazení dat.



Ukázkové dotazy

Zde jsou některé ukázky dotazů, které můžete použít k práci s databází:

- Zobrazit všechny studenty:

 SELECT * FROM Student;


- Zobrazit všechny kurzy:

SELECT * FROM Course;


- Zobrazit studenty a jejich kurzy:

SELECT s.jmeno, s.prijmeni, c.nazev_kurzu
FROM Student s
JOIN Student_Course_Signup scs ON s.student_id = scs.student_id
JOIN Course c ON scs.course_id = c.course_id;


- Zobrazit trenéry, kteří vyučují alespoň 2 kurzy:

SELECT * FROM trainers_teaching_atleast_2_courses;


Technologie

Projekt využívá:
- MySQL pro databázové úlohy.
- draw.io pro návrh ER diagramu.
- db-fiddle pro online práci s SQL dotazy.
