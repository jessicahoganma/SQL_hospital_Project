# hospital-database
SQL Statements For Hospital Database Example 

TO CREATE A TABLE*
CREATE TABLE psychologist (
    psy_id INT PRIMARY KEY
    psy_first_name VARCHAR (40)
    psy_last_name VARCHAR (40)
    psy_phone_num (INT)
    );


CREATE TABLE eval complete (
  patient_id INT,
  eval_id INT,
  PRIMARY KEY(patient_id, eval_id),
  FOREIGN KEY(patient_id) REFERENCES patient(patient_id) ON DELETE CASCADE, 
  FOREIGN KEY(eval_id) REFERENCES evaluation(eval_id) ON DELETE CASCADE
);
