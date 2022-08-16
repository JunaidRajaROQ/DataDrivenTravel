# Data Driven Travel
Create a Travel-app class and automate testing with data driven from SQL database<br>

[data types](https://www.w3schools.com/sql/sql_datatypes.asp),
[hsqldb](http://hsqldb.org/),
[java api](https://docs.oracle.com/javase/7/docs/api/),
[sql](https://www.w3schools.com/sql/)

## Steps
* Ensure the Eclipse IDE has Maven by looking for M2E from Help About ([details](https://www.vogella.com/tutorials/EclipseMaven/article.html))
* Install `DBViewer Plugin 1.2.2.v20101009` by ZIGEN from the Eclipse IDE marketplace
* Import into Eclipse as Git with smart import (accepting all defaults in wizard)
* Let the IDE finish building dependencies before proceeding (see bottom right of Eclipse)
* Run as JUnit test the file `TravelAppTest.java` for sanity testing the local database

## Database Schema

**Animal table**
- Hunger INT
- ID CHAR(36)
- Name VARCHAR(100)
- OwnerID CHAR(36)
- Species CHAR(1)
 
**Owner table**
- ID CHAR(36)
- Town VARCHAR(100)
- Name VARCHAR(100)

**To create the owner table**<br>
'CREATE TABLE Owner (ID CHAR(36), Town VARCHAR(100), Name VARCHAR(100), PRIMARY KEY(ID));'

**To create the animal table**<br>
'CREATE TABLE Animal (Hunger INT, ID CHAR(36), Name VARCHAR(100), OwnerID CHAR(36), Species CHAR(1), PRIMARY KEY(ID), FOREIGN KEY(OwnerID) REFERENCES Owner(ID));'

**To insert a new owner row** <br>
'INSERT INTO Owner(ID, Name, Town) VALUES ('11f3b90b-8214-4ec6-8cba-f1156d4e87f9', 'Junaid', 'Manchester');'

**To insert a new cat row** <br>
'INSERT INTO Animal (Hunger, ID, Name, OwnerID, Species) VALUES (0, 'b85ac401-932f-4997-8c99-87ddac0b7ec9', 'Cairo', '11f3b90b-8214-4ec6-8cba-f1156d4e87f9', 'C');'

**To insert a new dog row** <br>
'INSERT INTO Animal (Hunger, ID, Name, OwnerID, Species) VALUES (0, '4dc49a68-0471-4c49-8c96-b2f5ddf0c7cd', 'Rome', '11f3b90b-8214-4ec6-8cba-f1156d4e87f9', 'D');'

**To query an animal**<br>
'SELECT Hunger, ID, Species FROM Animal WHERE Name = 'Cairo';'

**To query all pets for an owner**
'SELECT animal.Name, animal.Species FROM Animal animal, Owner owner WHERE owner.Name = 'Junaid''
