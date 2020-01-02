## HOSPITAL MANAGEMENT SYSTEM

### feature 1: patient details

```sql
create table patient(
patient_id number not null primary key,
patientname varchar2(50) not null,
age number not null,
phone_no number unique,
admitted_for varchar2(20) not null,
specialization_id varchar2(20),
foreign key (specialization_id) references specializations(specializations_id)
);

create sequence patient_id start  with 100 increment by 1;

insert into patient(patient_id,patientname,age,phone_no,admitted_for,specialization_id)
values(patient_id.nextval,'john',10,8807544789,' stomach flu','S01');
insert into patient(patient_id,patientname,age,phone_no,admitted_for,specialization_id)
values(patient_id.nextval,'rock',42,7807544789,'TB','S02');
insert into patient(patient_id,patientname,age,phone_no,admitted_for,specialization_id)
values(patient_id.nextval,'jim',46,6807544789,'kidney disease','S03');
insert into patient(patient_id,patientname,age,phone_no,admitted_for,specialization_id)
values(patient_id.nextval,'harry',48,9807544789,'cataracts','S04');

select * from patient;

| patient_id | patientname | age | phone_no   | admitted_for   | specialization_id |
|------------|-------------|-----|------------|----------------|-------------------|
| 100        | john        | 10  | 8807544789 | stomach flu    | S01               |
| 101        | rock        | 42  | 7807544789 | TB             | S02               |
| 102        | jim         | 46  | 6807544789 | kidney disease | S03               |
| 103        | harry       | 48  | 9807544789 | cataracts      | S04               |

```

### feature2: list of doctors available for specific specializations: 

```sql

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

select * from doctors;

| doctor_id | doctorname | specialization_id |
|-----------|------------|-------------------|
| D01       | suraj      | S01               |
| D02       | vetri      | S02               |
| D03       | tamizh     | S03               |
| D04       | harish     | S04               |

```
### feature 3: list of specializations:
```sql

create table specializations(
specializations_id varchar2(10) primary key,
specialization_name varchar2(20) not null
);

insert into specializations values('S01','pediatrician');
insert into specializations values('S02','Cardiologist');
insert into specializations values('S03','Nephrologist');
insert into specializations values('S04','Ophthalmologist');

select * from specializations;


| specializations_id | specialization_name |
|--------------------|---------------------|
| S01                | pediatrician        |
| S02                | Cardiologist        |
| S03                | Nephrologist        |
| S04                | Ophthalmologist     |

```
### feature 4: list of medicines available:
```sql

create table tablets(
medicine_name varchar2(20),
quantity number not null ,
price number not null,
constraint qty_qty check (quantity>0)
);

insert into tablets(medicine_name,quantity,price)values('zophonile',250,10);
insert into tablets(medicine_name,quantity,price)values('calicop',150,6);
insert into tablets(medicine_name,quantity,price)values('nerozens',175,8);
insert into tablets(medicine_name,quantity,price)values('eyeons',200,9);

select * from tablets;


| medicine_name | quantity | price          |
|---------------|----------|----------------|
| zophonile     | 250      |    10          |
| calicop       | 150      |    6           |
| nerozens      | 175      |    8           |
| eyeons        | 200      |    9           |

```

### feature 5: prescription given to the patient

```sql
create table prescription(
patientname varchar2(50),
medicine_name varchar2(20) not null ,
no_tablets number not null,
price number 
);

insert into prescription (medicine_name,no_tablets,patientname) values('zophonile',10,'john');
insert into prescription (medicine_name,no_tablets,patientname) values('calicop',10,'rock');
insert into prescription (medicine_name,no_tablets,patientname) values('nerozens',10,'harry');
insert into prescription (medicine_name,no_tablets,patientname) values('eyeons',10,'jim');

```
### feature 6: updating the price column in prescription:

```sql
update prescription p
SET p.price = p.no_tablets * (select t.price from tablets t where p.medicine_name = t.medicine_name)
where medicine_name = (select medicine_name from tablets where medicine_name = p.medicine_name);


select * from prescription;


| patientname | medicine_name | no_tablets | price |
|-------------|---------------|------------|-------|
| john        | zophonile     | 10         | 100   |
| rock        | calicop       | 10         | 60    |
| harry       | nerozens      | 10         | 80    |
| jim         | eyeons        | 10         | 90    |

```
### feature 7: update the stock

```sql
update tablets t
set t.quantity = t.quantity-(select sum(p.no_tablets) from prescription p where p.medicine_name = t.medicine_name)
where medicine_name IN (select medicine_name from prescription p where p.medicine_name=t.medicine_name);

select * from tablets;

| medicine_name | quantity | price |
|---------------|----------|-------|
| zophonile     | 240      | 10    |
| calicop       | 140      | 6     |
| nerozens      | 165      | 8     |
| eyeons        | 190      | 9     |

```
### feature 8: update new stock :

```sql

--- update new stock
update tablets
set quantity=quantity+100
where medicine_name='eyeons';
select * from tablets;

| medicine_name | quantity | price |
|---------------|----------|-------|
| zophonile     | 240      | 10    |
| calicop       | 140      | 6     |
| nerozens      | 165      | 8     |
| eyeons        | 290      | 9     |

```
### select patientname from patient where age>40;
```
| patientname       |
|-------------------|
| jim               | 
| rock              | 
| harry             |                
```
### select * from patient where patientname = 'john';
```
| patient_id | patientname | age | phone_no   | admitted_for   | specialization_id |
|------------|-------------|-----|------------|----------------|-------------------|
| 100        | john        | 10  | 8807544789 | stomach flu    | S01               |

````
### select patientname from patient where ADMITTED_FOR ='TB';
```
| patientname       |
|-------------------|
| rock              | 

```
### SELECT doctorname from doctors where specialization_id ='S02';
```
| doctorname       |
|------------------|
| verti            | 
```
### select patient.*,doctors.* from patient inner join doctors on patient.specialization_id = doctors.specialization_id where patient_id=100;
```
| patient_id | patientname | age | phone_no   | admitted_for   | specialization_id | doctor_id | doctorname | specialization_id |
|------------|-------------|-----|------------|----------------|-------------------|-----------|------------|-------------------|
| 100        | john        | 10  | 8807544789 | stomach flu    | S01               | D01       | suraj      | S01               |


```
