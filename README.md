# AirBnB Clone (HBNB) - The Console

This team project mainly aims to update the Console part of a clone of [AirBnB](https://www.airbnb.com/).
This repository contains the initial stage of a student project to build and eventually deploy our server a clone of the AirBnB website. This stage implements a backend interface, or console, to manage program data. Console commands allow the user to create, update, and destroy objects, as well as manage file storage. Using a system of JSON serialization/deserialization, storage is persistent between sessions.

## Table of Content
* [Command Interpreter](#Command Interpreter)
* [Environment](#environment)
* [Environmental](#environmental Variables)
* [Descriptions](#Descriptions)
* [General Use](#General Use)
* [Available Models](#Available Models)
* [Testing(#Testing)
* [Examples(#examples)
* [Bugs](#bugs)
* [Authors](#authors)
* [License](#license)

## Environment
* Language: Python3
* OS: Ubuntu 14.04 LTS

## Environmental Variables

+ `HBNB_ENV`: The running environment. It can be `dev` or `test`.
+ `HBNB_MYSQL_USER`: The MySQL server username.
+ `HBNB_MYSQL_PWD`: The MySQL server password.
+ `HBNB_MYSQL_HOST`: The MySQL server hostname.
+ `HBNB_MYSQL_DB`: The MySQL server database name.
+ `HBNB_TYPE_STORAGE`: The type of storage used. It can be `file` (using `FileStorage`) or `db` (using `DBStorage`).

## Descriptions
Command Interpreter ([console.py](console.py))- Command interpreter(console) is a shell like with limited to a specific use-case. It can be used to test the functionality of the supported storage engines as well. You can find some examples of its usage [here](#examples). In this project the Command interpreter will help to manage the objects of our project, Like:
* To update/create a new object
* To retrive an object from a file, database, etc..
* To update attributes of an object
* To do operations on objects (count, compute stats, etc…)
* To destroy an object

List of commands this console current supports:
* `EOF` - exits console 
* `quit` - exits console
* `<emptyline>` - overwrites default emptyline method and does nothing
* `create` - Creates a new instance of`BaseModel`, saves it (to the JSON file) and prints the id
* `destroy` - Deletes an instance based on the class name and id (save the change into the JSON file). 
* `show` - Prints the string representation of an instance based on the class name and id.
* `count` - Return number of object instances by class.
* `all` - Prints all string representation of all instances based or not on the class name. 
* `update` - Updates an instance based on the class name and id by adding or updating attribute (save the change into the JSON file). 

## General Use
To start the command interpreter, follow these steps:
- Clone the project repository to your local machine and Navigate to the directory that contain the file.
 ```bash
git clone git@github.com:Mahari9/AirBnB_clone_v2.git
cd AirBnB_clone_v2
```
- Run the console.py file with: "./console.py" or "python console.py"
- When this command is run the following prompt should appear:
```
(hbnb)
```
- This prompt designates you are in the "HBnB" console. There are a variety of commands available within the console program.
- And finally type "help" in the console for documentation.

Interactive Mode
```bash
$ ./console.py
(hbnb) help
Documented commands (type help <topic>):
========================================
EOF  help  quit

(hbnb)
(hbnb)
(hbnb) quit
$
```
Non-Interactive Mode
```bash
$ echo "help" | ./console.py
(hbnb)

Documented commands (type help <topic>):
========================================
EOF  help  quit
(hbnb)
$
$ cat test_help
help
$
$ cat test_help | ./console.py
(hbnb)

Documented commands (type help <topic>):
========================================
EOF  help  quit
(hbnb)
$
```

## Available Models

These are the models that are currently available.

| Class | Description |
|:-|:-|
| BaseModel | A(n abstract) class that represents the base class for all models (all models are instances of this class). |
| User | Represents a user account. |
| State | Represents the geographical state in which a _User_ lives or a _City_ belongs to. |
| City | Represents an urban area in a _State_. |
| Amenity | Represents a useful feature of a _Place_. |
| Place | Represents a building containing rooms that can be rented by a _User_. |
| Review | Represents a review of a _Place_. |

## Testing
Within the project, we have incorporated unit tests to verify the accuracy of the implemented functionality. To execute these tests, follow the instructions below:
- "python3 -m unittest discover tests" (interactive mode)
- "echo 'python3 -m unittest discover tests' | bash" (Non-interactive mode)

## Examples

### Syntax

<br>
###### Example 0: Create an object
Usage: create <class_name>
```
(hbnb) create BaseModel
```
```
(hbnb) create BaseModel
3aa5babc-efb6-4041-bfe9-3cc9727588f8
(hbnb)
```

###### Example 1: Show an object
Usage: show <class_name> <_id>
```
(hbnb) show BaseModel 3aa5babc-efb6-4041-bfe9-3cc9727588f8
[BaseModel] (3aa5babc-efb6-4041-bfe9-3cc9727588f8) {'id': '3aa5babc-efb6-4041-bfe9-3cc9727588f8', 'created_at': datetime.datetime(2020, 2, 18, 14, 21, 12, 96959),
'updated_at': datetime.datetime(2020, 2, 18, 14, 21, 12, 96971)}
(hbnb)
```
###### Example 2: Destroy an object
Usage: destroy <class_name> <_id>
```
(hbnb) destroy BaseModel 3aa5babc-efb6-4041-bfe9-3cc9727588f8
(hbnb) show BaseModel 3aa5babc-efb6-4041-bfe9-3cc9727588f8
** no instance found **
(hbnb)
```
###### Example 3: Update an object
Usage: update <class_name> <_id>
```
(hbnb) update BaseModel b405fc64-9724-498f-b405-e4071c3d857f first_name "person"
(hbnb) show BaseModel b405fc64-9724-498f-b405-e4071c3d857f
[BaseModel] (b405fc64-9724-498f-b405-e4071c3d857f) {'id': 'b405fc64-9724-498f-b405-e4071c3d857f', 'created_at': datetime.datetime(2020, 2, 18, 14, 33, 45, 729889),
'updated_at': datetime.datetime(2020, 2, 18, 14, 33, 45, 729907), 'first_name': 'person'}
(hbnb)
```
</br>

### Alternative Syntax

<br>
###### Example 0: Show all User objects
Usage: <class_name>.all()
```
(hbnb) User.all()
["[User] (99f45908-1d17-46d1-9dd2-b7571128115b) {'updated_at': datetime.datetime(2020, 2, 19, 21, 47, 34, 92071), 'id': '99f45908-1d17-46d1-9dd2-b7571128115b', 'created_at': datetime.datetime(2020, 2, 19, 21, 47, 34, 92056)}", "[User] (98bea5de-9cb0-4d78-8a9d-c4de03521c30) {'updated_at': datetime.datetime(2020, 2, 19, 21, 47, 29, 134362), 'id': '98bea5de-9cb0-4d78-8a9d-c4de03521c30', 'created_at': datetime.datetime(2020, 2, 19, 21, 47, 29, 134343)}"]
```

###### Example 1: Destroy a User
Usage: <class_name>.destroy(<_id>)
```
(hbnb) User.destroy("99f45908-1d17-46d1-9dd2-b7571128115b")
(hbnb)
(hbnb) User.all()
(hbnb) ["[User] (98bea5de-9cb0-4d78-8a9d-c4de03521c30) {'updated_at': datetime.datetime(2020, 2, 19, 21, 47, 29, 134362), 'id': '98bea5de-9cb0-4d78-8a9d-c4de03521c30', 'created_at': datetime.datetime(2020, 2, 19, 21, 47, 29, 134343)}"]
```
###### Example 2: Update User (by attribute)
Usage: <class_name>.update(<_id>, <attribute_name>, <attribute_value>)
```
(hbnb) User.update("98bea5de-9cb0-4d78-8a9d-c4de03521c30", name "Todd the Toad")
(hbnb)
(hbnb) User.all()
(hbnb) ["[User] (98bea5de-9cb0-4d78-8a9d-c4de03521c30) {'updated_at': datetime.datetime(2020, 2, 19, 21, 47, 29, 134362), 'id': '98bea5de-9cb0-4d78-8a9d-c4de03521c30', 'name': 'Todd the Toad', 'created_at': datetime.datetime(2020, 2, 19, 21, 47, 29, 134343)}"]
```
###### Example 3: Update User (by dictionary)
Usage: <class_name>.update(<_id>, <dictionary>)
```
(hbnb) User.update("98bea5de-9cb0-4d78-8a9d-c4de03521c30", {'name': 'Fred the Frog', 'age': 9})
(hbnb)
(hbnb) User.all()
(hbnb) ["[User] (98bea5de-9cb0-4d78-8a9d-c4de03521c30) {'updated_at': datetime.datetime(2020, 2, 19, 21, 47, 29, 134362), 'name': 'Fred the Frog', 'age': 9, 'id': '98bea5de-9cb0-4d78-8a9d-c4de03521c30', 'created_at': datetime.datetime(2020, 2, 19, 21, 47, 29, 134343)}"]
```
</br>

## Bugs
No known bugs at this time. 

## Authors
Mahari Tsegay - [Github](https://github.com/Mahari9)
Abiel Iyasu - [Github](https://github.com/yafiet231)

## License
Public Domain. No copy write protection. 
