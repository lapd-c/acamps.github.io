---

---
select * from users limit 1;

alter table users
add column first_name_new varchar(48) encode bytedict;
alter table users
add column second_name_new varchar(48) encode bytedict;


update users
set 
    first_name_new = first_name,
  second_name_new = second_name;

alter table users
drop column first_name;
alter table users
rename column first_name_new to first_name;

alter table users
drop column second_name;
alter table users
rename column second_name_new to second_name;


