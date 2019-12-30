# instagram app

## Features
*users can create a new account 

### user account

create table acc(
user_id int,
username varchar2(30) not null,
birth_date date notnull,
constraint user_pk primary key(user_id);
);

create table mail(
user_id int,
mail_id varchar2(50),
constraint mail_pk primary key(mail_id)
);

create table password(
user_id int,
password varchar2(20) ,
constraint pass_pk primary key(password)
);


