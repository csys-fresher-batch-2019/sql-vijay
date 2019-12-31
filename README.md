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

insert into patient(patient_id,patientname,age,phone_no,admitted_for) values(100,'john',40,8807544789,' stomach flu');
insert into patient(patient_id,patientname,age,phone_no,admitted_for) values(101,'rock',42,8807544789,'TB');
insert into patient(patient_id,patientname,age,phone_no,admitted_for) values(102,'jim',46,8807544789,'kidney disease');
insert into patient(patient_id,patientname,age,phone_no,admitted_for) values(103,'harry',48,8807544789,'cataracts');
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


```


