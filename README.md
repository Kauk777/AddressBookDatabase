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
