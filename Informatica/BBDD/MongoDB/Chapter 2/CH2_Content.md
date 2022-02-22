# Chapter 2: Importing, Exporting, and Querying Data
En MongoDB trabajamos con documentos JSON
## JSON
**J**avascript **S**tandard **O**bject **N**otation

**JSON Format**
Start and end with curly braces ***{}***
Separate each ***key*** and ***value*** with a colon ***:***
Separate each ***key:value*** pair with a comma ***,***
***"keys"*** must be surrounded by quatation marks ***""***
▶ In MongoDB ***"keys"*** are called ***"fields"***

**e.g.**
```json
{
	"_id": 1,
	"name" : { "first" : "John", "last" : "Backus" },
	"contribs" : [ "Fortran", "ALGOL", "Backus-Naur Form", "FP" ],
	"awards" : [
		{
			"award" : "W.W. McDowell Award",
			"year" : 1967,
			"by" : "IEEE Computer Society"
		}, {
      		"award" : "Draper Prize",
      		"year" : 1993,
      		"by" : "National Academy of Engineering"
		}
 	]
}
```
Pros | Cons
:--:|:--:
Fiendly | Text-based
Readable | Space-consuming
Familiar | Limited
## BSON
**B**inary J**SON**
Bridges the gap between binary representation and JSON format.
Optimized for: 
- Speed
- Space
- Flexibility

Goal:
- High performance
- General-purpose focus

**JSON** | **BSON**
:--:|:--:
**Encoding**<br>UTF-8 String | **Encoding**<br>Binary
**Data Support**<br>String, Boolean, Number, Array | **Data Support**<br>String, Boolean, Number(Integer, Long, Float, ...), Array, Date, Raw Binary
**Readability**<br>Human and Machine | **Readability**<br>Machine Only 
	
![](https://i.imgur.com/hJ6DmzO.png)

###### Do [quiz](CH2_Quiz.md) 1 and 2.