## HOSPITAL MANAGEMENT SYSTEM

```sql
### patient details

create table patient(
patient_id number not null primary key,
patientname varchar2(50) not null,
age number not null,
phone_no number unique,
admitted_for varchar2(20) not null,
specialization_id varchar2(20),
foreign key (specialization_id) references specializations(specializations_id)
);

create sequence patient_id start with increment by 1;

insert into patient(patient_id,patientname,age,phone_no,admitted_for,specialization_id)
values(100,'john',40,8807544789,' stomach flu','S01');
insert into patient(patient_id,patientname,age,phone_no,admitted_for,specialization_id)
values(101,'rock',42,7807544789,'TB','S02');
insert into patient(patient_id,patientname,age,phone_no,admitted_for,specialization_id)
values(102,'jim',46,6807544789,'kidney disease','S03');
insert into patient(patient_id,patientname,age,phone_no,admitted_for,specialization_id)
values(103,'harry',48,9807544789,'cataracts','S04');

| patient_id | patientname | age | phone_no   | admitted_for   | specialization_id |
|------------|-------------|-----|------------|----------------|-------------------|
| 100        | john        | 40  | 8807544789 | stomach flu    | S01               |
| 101        | rock        | 42  | 7807544789 | TB             | S02               |
| 102        | jim         | 46  | 6807544789 | kidney disease | S03               |
| 103        | harry       | 48  | 9807544789 | cataracts      | S04               |
```
```sql
### list of doctors available for specific specializations: 
create table doctors(
doctor_id varchar2(10)  primary key,
doctorname varchar2(50) not null,
specialization_id varchar2(20),
foreign key (specialization_id) references specializations(specializations_id)
);

insert into doctors(doctor_id,doctorname,specialization_id)
values('D01','suraj','S01');
insert into doctors(doctor_id,doctorname,specialization_id)
values('D02','vetri','S02');
insert into doctors(doctor_id,doctorname,specialization_id)
values('D03','tamizh','S03');
insert into doctors(doctor_id,doctorname,specialization_id)
values('D04','harish','S04');

| doctor_id | doctorname | specialization_id |
|-----------|------------|-------------------|
| D01       | suraj      | S01               |
| D02       | vetri      | S02               |
| D03       | tamizh     | S03               |
| D04       | harish     | S04               |

```
```sql
### list of specializations:
create table specializations(
specializations_id varchar2(10) primary key,
specialization_name varchar2(20) not null
);

insert into specializations values(S01,'pediatrician');
insert into specializations values(S02,'Cardiologist');
insert into specializations values(S03,'Nephrologist');
insert into specializations values(S04,'Ophthalmologist');

| specializations_id | specialization_name |
|--------------------|---------------------|
| S01                | pediatrician        |
| S02                | Cardiologist        |
| S03                | Nephrologist        |
| S04                | Ophthalmologist     |

```
```sql
### list of medicines available:

create table medicine(
medicine_name varchar2(20) primary key,
quantity number not null,
disease_name varchar2(20) 
);

insert into medicine(medicine_name,quantity,disease_name)values('zophonile',250,'stomach flu');
insert into medicine(medicine_name,quantity,disease_name)values('calicop',150,'TB');
insert into medicine(medicine_name,quantity,disease_name)values('nerozens',175,'kidney disease');
insert into medicine(medicine_name,quantity,disease_name)values('eyeons',200,'cataracts');

| medicine_name | quantity | disease_name   |
|---------------|----------|----------------|
| zophonile     | 250      | stomach flu    |
| calicop       | 150      | TB             |
| nerozens      | 175      | kidney disease |
| eyeons        | 200      | cataracts      |

```



