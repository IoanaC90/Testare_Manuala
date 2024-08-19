<h1> Baza de date Club de fotbal</h1>

Aplicatia testata: Club de fotbal

Tool-ul utilizat: MySQL Workbench

Descrierea bazei de date: Baza de date este a unui club de fotbal pentru copii unde se tine evidenta copiilor,a parintilor,a echipamentelor primite,a taxei si a antrenorilor.

<ol>
<li>Schema bazei de date </li>
<br>
Mai jos gasiti schema bazei de date si contine toate tabelele si relatiile dintre ele

Tabelele sunt conectate intre ele astfel:

<ul>
  <li> Date copii  este conectata cu **nume tabela 2** through a **tip relatie** relationship which was implemented through **nume_tabela.nume_coloana_cheie_primara** as a primary key and **nume_tabela.nume_coloana_cheie_secundara** as a foreign key</li>
  <li> **nume tabela 3**  is connected with **nume tabela 4** through a **tip relatie** relationship which was implemented through **nume_tabela.nume_coloana_cheie_primara** as a primary key and **nume_tabela.nume_coloana_cheie_secundara** as a foreign key</li>
  <li> **nume tabela 5**  is connected with **nume tabela 6** through a **tip relatie** relationship which was implemented through **nume_tabela.nume_coloana_cheie_primara** as a primary key and **nume_tabela.nume_coloana_cheie_secundara** as a foreign key</li>
  ...........
  <li> **nume tabela n**  is connected with **nume tabela n+1** through a **tip relatie** relationship which was implemented through **nume_tabela.nume_coloana_cheie_primara** as a primary key and **nume_tabela.nume_coloana_cheie_secundara** as a foreign key</li>
</ul><br>

<li>Queriuri</li><br>

<ol type="a">
  <li>DDL (Data Definition Language)</li>


  Urmatoarele instructiuni au fost scrise pentru a crea baza de date si tabelele (INSTRUCTIUNUI DE CREARE)
  
create database Club_de_fotbal;

create table Date_copii(
ID int unsigned auto_increment primary key,
Nume varchar(20) not null,
Prenume varchar(20) not null,
Data_nasterii date not null
);

create table Date_parinti(ID int primary key not null,Nume varchar(20) not null,Prenume varchar(20) not null,Numar_telefon varchar(10),
ID_copil int not null);

create table Echipamente
(ID int primary key not null,
Marime varchar(10),
Nume_inscriptionat varchar(10),
Numar_inscriptionat int,
ID_copil int not null,
foreign key (ID_copil) references Date_copii(ID_copil));

create table Taxa
(ID int primary key not null,
ID_copil int not null,
Ianuarie varchar(10),
Februarie varchar(10),
Martie varchar(10),
Aprilie varchar(10),
Mai varchar(10),
Iunie varchar(10),
Iulie varchar(10),
August varchar(10),
Septembrie varchar(10),
Octombrie varchar(10),
Noiembrie varchar(10),
Decembrie varchar(10),
foreign key(ID_copil) references Date_copii(ID_copil));

create table Antrenori
(ID int primary key not null auto_increment,
Nume_antrenor varchar(10),
Prenume_antrenor varchar(10),
Numar_telefon varchar(13));

  Dupa ce am creat baza de date si tabelele, cateva insctructiuni ALTER au fost scrise pentru a schimba structura bazei de date asa cum sunt descrise mai jos:

  alter table Date_copii add column ID_antrenor int not null;
  alter table Date_copii add foreign key (ID_antrenor) references Antrenor(ID);
  Alter table Date_parinti add foreign key (ID_copil) references Date_copii(ID_copil);


  

  **Inserati aici toate instructiunile de ALTER pe care le-ati scris. Incercati sa includeti instructiuni cat mai variate cum ar fi:**
 **- schimbare nume tabela**
 **- redenumire coloana**
 **- adaugare proprietati coloana (ex: adaugare auto-increment)**
 **- modificare proprietati coloana (ex: modificare tip de data, modificare pozitie coloana etc)*
 
  
  <li>DML (Data Manipulation Language)</li>

  Pentru a putea utiliza baza de date am inserat in tabelele diverse date necesare pentru a efectua interogări și a manipula datele. 
  În procesul de testare, aceste date necesare sunt identificate în faza de proiectare a testului și create în faza de implementare a testului. 

  Mai jos puteti gasi toate instructiunile de inserare a datelor care au fost create in acest proiect:

  insert into Date_copii (Nume,Prenume,Data_nasterii) values ('Craciun','Sebastian','2019-01-19');
  insert into Date_copii (Nume,Prenume,Data_nasterii) values 
  ('Badea','Filip','2019-01-17'),
  ('Pruteanu','Andrei','2019-01-18'),
  ('Gache','Razvan','2019-01-18'),
  ('Neagu','Teodor','2019-02-25'),
  ('Mihai','Gabi','2019-03-12'),
  ('Bucatariu','David','2019-10-10'),
  ('Muresan','Patrick','2019-10-14'),
  ('Babos','Patrick','2019-12-12');

insert into Date_parinti values
(1,'Craciun','Ioana','0773974717',1),
(2,'Badea','Lucian','0751127286',2),
(3,'Bucatariu','Madalina','0747222111',7),
(4,'Neagu','Razvan','0778555111',5),
(5,'Mihai','Razvan','0747555444',6),
(6,'Craciun','Adrian','0777125286',1);

insert into Echipamente
 values(1,'s','Sebi',19,1),
 (2,'XS','Andrei',12,3),
 (3,'M','David',11,7),
 (4,'s','Gabi',15,6),
 (5,'s','Patrick',10,8),
 (6,'xs','Teo',1,5);

 insert into Taxa 
values(1,1,'Achitat','Achitat','Achitat','Achitat','Achitat','Achitat','Achitat','Achitat','Achitat','Achitat','Achitat','Achitat'),
(2,2,'Achitat','Achitat','Achitat','Achitat','Achitat','Neachitat','Achitat','Achitat','Achitat','Achitat','Achitat','Achitat'),
(3,5,'Achitat','Achitat','Achitat','Neachitat','Neachitat','Achitat','Achitat','Achitat','Achitat','Achitat','Achitat','Achitat'),
(4,4,'Achitat','Achitat','Achitat','Achitat','Achitat','Achitat','Achitat','Achitat','Achitat','Achitat','Achitat','Achitat'),
(5,9,'Neachitat','Neachitat','Achitat','Achitat','Achitat','Achitat','Achitat','Achitat','Achitat','Achitat','Achitat','Achitat');

insert into Antrenori (Nume_antrenor,Prenume_antrenor,Numar_telefon) 
values ('Ciocan','Cristian','0741222545'),
('Darstar','Liviu','0751124356'),
('Marin','Gheorghe','0789254631');

  După inserare, pentru a pregăti datele pentru a fi mai potrivite pentru procesul de testare, am actualizat câteva date în felul următor:

update Date_copii set ID_antrenor='1' where(ID_copil=1) or (ID_copil=3) or (ID_copil=6) or (ID_copil=5);
update Date_copii set ID_antrenor='3' where (ID_copil=2) or (ID_copil=4) or (ID_copil=7) or (ID_copil=8);
update Date_copii set ID_antrenor='2' where ID_copil=9;

  <li>DQL (Data Query Language)</li>

După procesul de testare, am șters datele care nu mai erau relevante pentru a păstra baza de date curată: 

delete from Taxa where id=5;
drop table Taxa;
drop table Echipamente;
drop table Meciuri;

Pentru a simula diverse scenarii care s-ar putea întâmpla în viața reală, am creat următoarele interogări care ar acoperi mai multe situații potențiale din viața reală:

select * from Date_copii;

select * from Date_parinti;

select * from Echipamente;

select * from Taxa;

select * from Antrenori;

select * from Date_copii cross join Date_parinti on Date_copii.ID_copil=Date_parinti.ID_copil;

select * from Date_copii inner join Echipamente on Date_copii.ID_copil=Echipamente.ID_copil;

select * from Date_copii left join Date_parinti on Date_copii.ID_copil=Date_parinti.ID_copil where Date_parinti.Nume='Craciun';

select Nume,Prenume from Date_copii order by Nume;

select * from Date_copii order by Date_copii.data_nasterii;

select Nume,prenume,ID_antrenor from Date_copii where id_antrenor=2;

select Nume_antrenor,Prenume_antrenor from Antrenori where Nume_antrenor like '%an';

<br>

**- AND**<br>
**- OR**<br>
**- NOT**<br>
**- like**<br>
**- functii agregate**<br>
**- group by**<br>
**- having**<br>
**- OPTIONAL DAR RECOMANDAT: Subqueries - nu au fost in scopul cursului. Puteti sa consultati tutorialul [asta](https://www.techonthenet.com/mysql/subqueries.php) si daca nu intelegeti ceva contactati fie trainerul, fie coordonatorul de grupa**<br>


</ol>
