# AirBnB Clone (HBNB) - The Console

This team project mainly aims to update the Console part of a clone of [AirBnB](https://www.airbnb.com/).
This repository contains the initial stage of a student project to build and eventually deploy our server a clone of the AirBnB website. This stage implements a backend interface, or console, to manage program data. Console commands allow the user to create, update, and destroy objects, as well as manage file storage. Using a system of JSON serialization/deserialization, storage is persistent between sessions.

## Table of Content
* [Environment](#Environment)
* [Environmental Variables](#Environmental-Variables)
* [Descriptions](#Descriptions)
* [General Use](#General-Use)
* [Available Models](#Available-Models)
* [Testing](#Testing)
* [Examples](#examples)
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
```
root@f752e78ea6ed:~/AirBnB_clone_v3# ./console.py
(hbnb) all MyModel
** class doesn't exist **
(hbnb) create BaseModel
7da56403-cc45-4f1c-ad32-bfafeb2bb050
(hbnb) all BaseModel
[[BaseModel] (7da56403-cc45-4f1c-ad32-bfafeb2bb050) {'updated_at': datetime.datetime(2017, 9, 28, 9, 50, 46, 772167), 'id': '7da56403-cc45-4f1c-ad32-bfafeb2bb050', 'created_at': datetime.datetime(2017, 9, 28, 9, 50, 46, 772123)}]
(hbnb) show BaseModel 7da56403-cc45-4f1c-ad32-bfafeb2bb050
[BaseModel] (7da56403-cc45-4f1c-ad32-bfafeb2bb050) {'updated_at': datetime.datetime(2017, 9, 28, 9, 50, 46, 772167), 'id': '7da56403-cc45-4f1c-ad32-bfafeb2bb050', 'created_at': datetime.datetime(2017, 9, 28, 9, 50, 46, 772123)}
(hbnb) destroy BaseModel 7da56403-cc45-4f1c-ad32-bfafeb2bb050
(hbnb) show BaseModel 7da56403-cc45-4f1c-ad32-bfafeb2bb050
** no instance found **
(hbnb) quit
```
## Bugs
No known bugs at this time. 

## Authors
- Mahari Tsegay - [Github](https://github.com/Mahari9)
- Abiel Iyasu - [Github](https://github.com/yafiet231)

## License
Public Domain. No copy write protection. 
