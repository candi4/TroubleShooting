# YAML
How to use YAML via Python

## Read `.yaml` file
```python
import yaml
with open("parameters.yaml", "r") as file:
    params = yaml.safe_load(file)
voxel_size = params["voxel_size"]
object_filenames = params['object_filenames']
```
## Structure of YAML
An example of `.yaml` file:
```yaml
#Comment: Student record
#Describes some characteristics and preferences
---
name: Martin D'vloper #key-value
age: 26
hobbies: 
  - painting #first list item
  - playing_music #second list item
  - cooking #third list item
programming_languages:
  java: Intermediate
  python: Advanced
  javascript: Beginner
favorite_food: 
  - vegetables: tomatoes 
  - fruits: 
      citrics: oranges 
      tropical: bananas
      nuts: peanuts
      sweets: raisins
```
The result of reading the file in python:
```python
[
    {
        "name": "Martin D'vloper",
        "age": 26,
        "hobbies": ["painting", "playing_music", "cooking"],
        "programming_languages": {
            "java": "Intermediate",
            "python": "Advanced",
            "javascript": "Beginner",
        },
        "favorite_food": [
            {"vegetables": "tomatoes"},
            {
                "fruits": {
                    "citrics": "oranges",
                    "tropical": "bananas",
                    "nuts": "peanuts",
                    "sweets": "raisins",
                }
            },
        ],
    }
]
```
## Type of datas in `.yaml` in python
In `.yaml`:
```yaml
array1:
  - - 1
    - 2
    - 3
  - - 4
    - -5
    - 6.2
    - word
array2:
  [[1, 2, 3], 
   [4, -5, 6.2, 'word']]
```
In python:
```python
{'array1': [[1, 2, 3], [4, -5, 6.2, 'word']], 
 'array2': [[1, 2, 3], [4, -5, 6.2, 'word']]}
```
## References
* [YAML이란?](https://www.redhat.com/ko/topics/automation/what-is-yaml)
* [YAML Format Tutorial](https://cantera.org/tutorials/yaml/yaml-format.html)
