#EasyCRUD

RetardORM is a class which you can use to easily execute basic SQL operations like(insert, update, select, delete) on your database. 
It uses the database class you've created to execute the SQL queries.

Actually it's just a little ORM class.

## How to use RetardORM
#### 1. First, create a new class. Then require the RetardORM class.
#### 2. Extend your class to the base class RetardORM and add the following fields to the class.
#### Example class :
```php
<?php
require_once("RetardORM.php");
 
class YourClass  Extends RetardORM
{
 
  # The table you want to perform the database actions on
  protected $table = 'persons';

  # Primary Key of the table
  protected $pk  = 'id';
  
}
```

## RetardORM in action.

#### Creating a new person
```php
<?php
// First we"ll have create the instance of the class
$person = new person();
 
// Create new person
$person->Firstname  = "Kona";
$person->Age        = "20";
$person->Sex        = "F";
$created            = $person->Create();
 
//  Or give the bindings to the constructor
$person  = new person(array("Firstname"=>"Kona","age"=>"20","sex"=>"F"));
$created = $person->Create();
 
// SQL Equivalent
"INSERT INTO persons (Firstname,Age,Sex) VALUES ('Kona','20','F')"
```
#### Deleting a person
```php
<?php
// Delete person
$person->Id  = "17";
$deleted     = $person->Delete();
 
// Shorthand method, give id as parameter
$deleted     = $person->Delete(17);
 
// SQL Equivalent
"DELETE FROM persons WHERE Id = 17 LIMIT 1"
```
#### Saving person's data
```php
<?php
// Update personal data
$person->Firstname = "John";
$person->Age  = "20";
$person->Sex = "F";
$person->Id  = "4"; 
// Returns affected rows
$saved = $person->Save();
 
//  Or give the bindings to the constructor
$person = new person(array("Firstname"=>"John","age"=>"20","sex"=>"F","Id"=>"4"));
$saved = $person->Save();
 
// SQL Equivalent
"UPDATE persons SET Firstname = 'John',Age = 20, Sex = 'F' WHERE Id= 4"
```
#### Finding a person
```php
<?php
// Find person
$person->Id = "1";
$person->find();

echo $person->Firstname;
// Johny
 
// Shorthand method, give id as parameter
$person->find(1); 
 
// SQL Equivalent
"SELECT * FROM persons WHERE Id = 1"
```
#### Getting all the persons
```php
<?php
// Finding all person
$persons = $person->all(); 
 
// SQL Equivalent
"SELECT * FROM persons 
```

