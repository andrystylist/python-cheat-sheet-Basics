# The Basics python-cheat-sheet (part 1)

***Creator: Andry Peña*** 
 
### print()-> print to screen, Since it is a function, it is always used with parentesis()

| Main data types | Example | important |
| --- | --- | --- | 
| bool | ```a: bool = False``` ```b: bool = True``` ```Print(a, b)``` ```False True``` |
| int | ```a: int = 10``` ```print(a)``` ```10``` |
| float | ```a: int = 10.10``` ```print(a)``` ```10.10``` |
| str |  ```a: str = "Hi" ``` ```print(a)``` ```Hi``` | String variables are enclosed in double quotes "text" or single quotes 'text' for multi-line text strings """ text""" is used.
|  |  ```a: str = """Hi""" ``` ```print(a)``` ```Hi``` | 
|  |  ```a: str = 'Hi'``` ```print(a)``` ```Hi``` | 
|list | ```d: list = [1, 3.2, [3, 2], "w"]``` ```print(d)``` ```[1, 3.2, [3, 2], 'w']```| Accepts repeated data, its elements are mutable, they are accessible through the index
| set | ```d: set = {1, 1, 3, 4}``` ```print(d)``` ```{1, 3, 4}``` | Removes repeated values from the list, the set does not accept repeated data, its elements are immutable, they are not accessible by the index.
| dict |```d: dict = {1: "one", 2: "two"}``` ```print(d)``` ```{1: 'one', 2: 'two'}```  | Keys of immutable types, unique (does not support repeats) are accessible by key, support repeated values
| tuple | ```d: tuple = ("w",1, 1, 3)``` ```print(d)``` ```('w',1, 1, 3)``` |Accepts repeated data, its elements are immutable, they are accessible by the index
