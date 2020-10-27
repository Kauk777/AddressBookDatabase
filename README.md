# Address Book Database

## UC1 

> Creating AddressBook Database

`CREATE DATABASE addressbook_service;`

> Using Database

`USE addressbook_service;`

## UC2

> Creating AddressBook table

```
CREATE TABLE address_book 
(
  firstName  VARCHAR(150) NOT NULL,
  lastName   VARCHAR(150) NOT NULL,
  address    VARCHAR(300) NOT NULL,
  city       VARCHAR(150) NOT NULL,
  state      VARCHAR(150) NOT NULL,
  zip        INT(6) unsigned,
  phone      INT(10) unsigned,
  email      VARCHAR(150) NOT NULL
);

```
> Describing address_book table

`DESCRIBE address_book;`

## UC3

> Insert new contacts in address_book

```
INSERT INTO address_book VALUES 
 ('Paul','Fitzer','Mave Hill 205','Los Angels','California',501002,129875634,'paul77@gmail.com'),
 ('Sidh','Veneet','Kali Marg 41','Kolkata','West Bengal',704106,700160125,'veeentsdh@hotmail.com'),
 ('Vansikha','Rajput','South Delhi 54 street','New Delhi','Delhi',201456,987152634,'sikhavan@gamil.com'),
 ('Alzaria','Putossa','Fire Hill 4010','Queens','New York',101256,124578962,'putossa78@gmail.com'),
 ('Aarav','Aryan','Peacock street 750','New Delhi','Delhi',201256,884578962,'aryan18@gmail.com'),
 ('Hopiux','Carla','Soft Corner Block','Virginia City','Nevada',304456,484566962,'carla@gmail.com');
```
> showing records

`SELECT * FROM address_book;`

## UC4

> Editing exsisting contact by person name

```
UPDATE address_book SET 
email='fitzer43@gamil.com', 
city='Las vegas', 
state='Nevada',
zip=602301
WHERE firstName='Paul' AND lastName='Fitzer';
```

## UC5

> Deleting contact by person name

`DELETE FROM address_book WHERE firstName='Sidh' AND lastName='Veneet';`

## UC6

> Retrieving records of person belonging to a city or state

`SELECT * FROM address_book WHERE city='Las Vegas' OR state='Nevada';`

## UC7

> Size of addressbook by city or state

`SELECT city,COUNT(city) FROM address_book GROUP BY city;`

`SELECT state,COUNT(state) FROM address_book GROUP BY state;`

## UC8

> Retrieve entries sorted alphabetically by person's name for given city

`SELECT * FROM address_book WHERE city='New Delhi' ORDER BY firstName;`
