## HOSPITAL MANAGEMENT SYSTEM

### feature 1: patient registration

```sql
create table patientReg(
patient_id number primary key ,
patientname varchar2(50) not null,
adharcardno number ,
dob date,
gender varchar2(20) ,
phoneno number not null,
patientreg_date date 
);

create sequence patient_id start with 40 increment by 1;

```

patient_id | patientname | adharcard no     | dob        | gender | phone no   | patientreg_date  |
40         |  Manoj      | 1092837465091283 | 12-12-1999 | M      | 8976543456 | 20-12-2019       |
41         |  aravinth   | 7845372891029384 | 16-08-1998 | M      | 7382910348 | 25-12-2019       |

### feature 2: Appointment list
```
create table appointment(     
app_id number primary key,
patient_id number not null,
purpose varchar2(50)not null,
doctor_id number not null,
app_date date not null,
app_time varchar2(20) not null,
status varchar2(50) default 'pending',
visited varchar2(10) default 'no',
foreign key (patient_id) references patientReg(patient_id),
foreign key (doctor_id) references doctorlist(doctor_id)  
);


insert into appointment(app_id,patient_id,purpose,doctor_id,app_date,app_time)values(657483,40,'fever',1001,TO_DATE('2020-02-20','yyyy-mm-dd'),'10:00' );
```

| app_id | patient_id | purpose      | doctor_id   | app_date   | app_time |
|--------|------------|--------------|-------------|------------|----------|
|657483  | 40         |heart problem |    102      |2020-02-20  | 10:00    |


### feature 3: list of doctors available for specific specializations: 

```sql

drop table doctorlist;
create table doctorlist(
doctor_id number primary key,
doctor_name varchar2(40) not null,
splzation_id number not null,
consultingfee number not null,
foreign key (splzation_id) references splzations(splzation_id)
);

insert into doctorlist(doctor_id,doctor_name,splzation_id,consultingfee) values(1002,'suraj',102,300);
insert into doctorlist(doctor_id,doctor_name,splzation_id,consultingfee) values(1001,'kumar',101,500);


select * from doctorlist;
```
| doctor_id | doctorname | specialization_id | consultingfee |
|-----------|------------|-------------------|---------------|
| 1001      | suraj      | 101               |    300        |
| 1002      | vetri      | 102               |    500        |



### feature 4: list of specializations:
```sql

create table splzations(
splzation_id number primary key,
splzation_name varchar2(20) not null
);

insert into splzations values('101','pediatrician');
insert into splzations values('102','Cardiologist');

select * from splzations;

```
| splzation_id | splzation_name |
|--------------|----------------|
| 101          | pediatrician   |
| 102          | Cardiologist   |



### feature 5: Rating :
```sql

create table rating(
patient_id number not null,
doctor_id number not null,
rating float not null,
foreign key (patient_id) references patientReg(patient_id),
foreign key (doctor_id) references doctorlist(doctor_id)
);

select * from rating
```

| patient_id    | doctor_id| rating         |
|---------------|----------|----------------|
| 40            | 1002     |    10          |
| 41            | 1002     |    8           |




### feature 6: prescription given to the patient

```sql
create table prescription(
prescription_id number primary key,
patient_name varchar2(50) not null,
doctorname varchar2(50) not null,
comments varchar2(100) not null,
total_amt number
);

create sequence prescription_id start with 1 increment by 1;


insert into prescription(prescription_id,patient_name,doctorname,comments)values(prescription_id.nextval,'manoj','suraj','take medicine regularly');


```

| prescription_id | patient_name | doctorname | comments                | total_amt |
|-----------------|--------------|-----------:|-------------------------|-----------|
| 1               | Manoj        |      suraj | take medicine regularly | 500       |



### feature 7: Overall rating:
```
create table overallrating(
doctor_id number,
rating float,
foreign key(doctor_id) references doctorlist(doctor_id)
);

```
| doctor_id | rating | 
|-----------|--------|
| 1002      |     9  |
