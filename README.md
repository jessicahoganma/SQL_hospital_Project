SQL Hospital Project

-- Creating the tables --

CREATE TABLE psychologist (
  psy_id INT PRIMARY KEY,
  first_name VARCHAR(40) NOT NULL,
  last_name VARCHAR(40) NOT NULL,
  phone_no VARCHAR(20) NOT NULL,
  );

CREATE TABLE hospital (
  hosp_id INT PRIMARY KEY,
  hosp_address VARCHAR(40) NOT NULL,
  hosp_name VARCHAR(60) NOT NULL,
  hosp_phone_num VARCHAR(20)
);

CREATE TABLE patient (
  patient_id INT PRIMARY KEY,
  first_name VARCHAR(40) NOT NULL,
  last_name VARCHAR(40) NOT NULL,
  dob VARCHAR(20),
);

CREATE TABLE evaluation (
  eval_id INT PRIMARY KEY,
  result VARCHAR(40) NOT NULL,
);

-- Altering the tables to establish the relationships via FOREIGN KEYs

ALTER TABLE patient
ADD FOREIGN KEY(hospital)
REFERENCES client(hosp_id)
ON DELETE SET NULL;

ALTER TABLE evaluation
ADD FOREIGN KEY(psychologist)
REFERENCES teacher(psy_id)
ON DELETE SET NULL;

ALTER TABLE evaluation
ADD FOREIGN KEY(hospital)
REFERENCES client(hosp_id)
ON DELETE SET NULL;



CREATE TABLE eval_received (
  patient_id INT,
  eval_id INT,
  PRIMARY KEY(patient_id, eval_id),
  FOREIGN KEY(patient_id) REFERENCES patient(patient_id) ON DELETE CASCADE,
  FOREIGN KEY(eval_id) REFERENCES course(eval_id) ON DELETE CASCADE
);


-- Populating the tables

INSERT INTO psychologist VALUES
(1,'Daryl','Powers','309-385-5499'),
(2,'Russell','Ross','814-328-1181'),
(3,'Regina','Cornell','717-634-9154'),
(4,'Tonya','Robbins','952-876-8377'),
(5,'Reyna','Kantor','435-335-3771'),
(6,'Marilyn ','Banks','864-649-2679'),
(7,'Barton','Conklin','276-773-4278'),
(8,'Martha','Harvey','916-799-4513'),
(9,'Kenneth','Steel','215-810-6001'),
(10,'Richard','Bell','765-425-3764');


INSERT INTO hospital VALUES
(101,'3628 Berry Street','Springfield','719-579-9842'),
(102,'835 Orchard Street','St Elizabeth','952-851-1005'),
(103,'2588 Franklin Avenue','Cambridge','361-878-2670'),
(104,'348 Harry Place','Overland Park','704-766-8113'),
(105,'2382 Retreat Avenue','Butler','205-289-4490'),
(106,'1726 Hilltop Street','Skellytown','413-736-6939'),
(107,'4574 Oak Ridge Drive','Meriden','573-493-8969'),
(108,'108 Pearlman Avenue','Overland Park','978-219-5848'),
(109,'4647 Better Street','Springfield','913-339-5876'),
(110,'1426 Shinn Avenue','Cambridge','724-477-6047');


INSERT INTO patient VALUES
(101,'Sandra','Andrzejewski','1958-10-10',103),
(102,'Shane','Campbell','1940-04-06',108),
(103,'Marilyn','Hays','1957-02-17',110),
(104,'Theresa','Scherr','1961-06-11',101),
(105,'Barbara','Rodriguez','1977-08-31',109),
(106,'William','Adkins','1973-06-28',105),
(107,'Kathleen','Sandoval','1971-06-05',109),
(108,'Brian','Townsend','1946-08-15',105),
(109,'Wilma','Peraza','1956-08-12',109),
(110,'Sean','Aleman','1947-09-08',102);


INSERT INTO evalaution VALUES
(11,'Negative',102,1),
(12,'Positive',108,5),
(13,'Positive',102,7),
(14,'Positive',103,1),
(15,'Negative',106,4),
(16,'Positive',105,6),
(17,'Negative',103,5),
(18,'Negative',104,2),
(19,'Negative',105,3),
(20,'Negative',107,6);

INSERT INTO takes_course VALUES
(101,11),
(102,11),
(107,11),
(103,12),
(105,12),
(107,12),
(101,13),
(103,13),
(104,13),
(105,14),
(109,14),
(101,15),
(102,15),
(106,15),
(101,16),
(107,16),
(110,16),
(105,17),
(106,17),
(108,17),
(110,17),
(102,18),
(106,18),
(108,18),
(109,18),
(103,19),
(105,19),
(106,19),
(109,19),
(110,19),
(101,20),
(104,20),
(107,20);
