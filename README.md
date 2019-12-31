# Hospital management system

### Feature 1: view the list of patients admitted

``` sql

create table patient(
patient_id int unique not null,
patientname varchar2(50) not null,
age int not null,
phone_no int unique;
admitted_for varchar2(20) not null
);

create sequence patient_id start with increment by 1;

insert into patient(patient_id,patientname,age,phone_no,admitted_for,consulting_doc) values(100,'john',40,8807544789,' stomach flu','Pediatrician');
insert into patient(patient_id,patientname,age,phone_no,admitted_for,consulting_doc) values(101,'rock',42,7807544789,'TB','Cardiologist');
insert into patient(patient_id,patientname,age,phone_no,admitted_for,consulting_doc) values(102,'jim',46,6807544789,'kidney disease','Nephrologist');
insert into patient(patient_id,patientname,age,phone_no,admitted_for,consulting_doc) values(103,'harry',48,9807544789,'cataracts','Ophthalmologist');

| patient_id | patientname | age | phone_no   | admitted_for   |
|------------|-------------|-----|------------|----------------|
| 100        | john        | 40  | 8807544789 | stomach flu    |
| 101        | rock        | 42  | 7807544789 | TB             |
| 102        | jim         | 46  | 6807544789 | kidney disease |
| 103        | harry       | 48  | 9807544789 | cataracts      |

 ```
 ### feature 2: list of doctors

```sql

create table doctor(
doctor_id varchar2(10) unique not null,
doctorname varchar2(50) not null,
specialization varchar2(20) not null
);

insert into doctors(doctor_id,doctorname,specialization)values('D01','suraj','Pediatrician');
insert into doctors(doctor_id,doctorname,specialization)values('D02','vetri','Cardiologist');
insert into doctors(doctor_id,doctorname,specialization)values('D03','tamizh','Nephrologist');
insert into doctors(doctor_id,doctorname,specialization)values('D04','harish','Ophthalmologist');

| doctor_id | doctorname | specialization  |
|-----------|------------|-----------------|
| D01       | suraj      | Pediatrician    |
| D02       | vetri      | Cardiologist    |
| D03       | tamizh     | Nephrologist    |
| D04       | harish     | Ophthalmologist |

```
### medicine shop
```sql

create table medicine(
medicine_name varchar2(20),
quantity number 
);

insert into (medicine_name,quantity)values('zophonile',250);
insert into (medicine_name,quantity)values('calicop',150);
insert into (medicine_name,quantity)values('nerozens',175);
insert into (medicine_name,quantity)values('eyeons',200);

| medicine_name | quantity |
|---------------|----------|
| zophonile     | 250      |
| calicop       | 150      |
| nerozens      | 175      |
| eyeons        | 200      |

```

