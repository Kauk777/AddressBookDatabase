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

## UC9

> Adding type field in addressbook

`ALTER TABLE address_book ADD type VARCHAR(20);'

> Adding type values in record

```
UPDATE address_book SET 
type='Friends' WHERE firstName IN('Paul','vansikha','Aarav');
```

```
UPDATE address_book SET 
type='Family' WHERE firstName='Hopiux';
```
```
UPDATE address_book SET 
type='Profession' WHERE firstName='Alzaria';
```

## UC10

> Number of contact by type

`SELECT type,COUNT(type) FROM address_book GROUP BY type;`

## UC11

> Adding person contact to both friend and family

```
INSERT INTO address_book VALUES 
('Sidh','Veneet','Kali Marg 41','Kolkata','West Bengal',704106,700160125,'veeentsdh@hotmail.com','Friends'),
('Joshua','Bob','Mave Hill 205','Los Angels','California',501002,129875634,'paul77@gmail.com','Family');
```

## UC12

> ER Model: Entity

***Contact***

```
CREATE TABLE contacts 
(
ContactId  INT PRIMARY KEY,
FirstName  VARCHAR(200) NOT NULL,
LastName  VARCHAR(200) NOT NULL,
Address   VARCHAR(200) NOT NULL,
Zip       INT NOT NULL,
FOREIGN KEY(Zip) REFERENCES zip_location(Zip)
);
```

***ZipLocation***


```
CREATE TABLE zip_location 
(
Zip  INT NOT NULL PRIMARY KEY,
City VARCHAR(200) NOT NULL,
State VARCHAR(200) NOT NULL
);
```

***phone***


```
CREATE TABLE phone_contact 
(
ContactId  INT,
PhoneType  VARCHAR(200) NOT NULL,
Number   VARCHAR(10) NOT NULL,
PRIMARY KEY(ContactId,PhoneType,Number),
FOREIGN KEY(ContactId) REFERENCES contacts(ContactId)
);
```

***Email***


```
CREATE TABLE email_contact 
(
ContactId  INT,
EmailType  VARCHAR(200) NOT NULL,
Email    VARCHAR(200) NOT NULL,
PRIMARY KEY(ContactId,EmailType,Email),
FOREIGN KEY(ContactId) REFERENCES contacts(ContactId)
);
```

***Type***

```
CREATE TABLE type 
(
ContactId  INT,
Type  VARCHAR(150) NOT NULL,
PRIMARY KEY(ContactId,Type),
FOREIGN KEY(ContactId) REFERENCES contacts(ContactId)
);
```

> Attributes: Composite

***Zip***

> Attributes: Multi-Valued

***Phone***

***Type***

***Email***







