# instagram app

## Features
*users can create a new account 

### user account

``` sql

create table acc(
user_id int,
username varchar2(30) not null,
birth_date date not null,
mail_id varchar2(50) not null UNIQUE,
password varchar2(20),
constraint user_pk primary key(user_id)
);
 ```


