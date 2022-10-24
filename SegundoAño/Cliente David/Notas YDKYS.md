# Chapter 7
```js
var Student = (function defineStudent(){
	var records = [
		{ id: 14, name: "Kyle", grade: 86 },
		{ id: 73, name: "Suzy", grade: 87 },
		{ id: 112, name: "Frank", grade: 75 },
		{ id: 6, name: "Sarah", grade: 91 }
	];
	
	var publicAPI = {
		getName
	};
	
	return publicAPI;
	
	// ************************
	
	function getName(studentID) {
		var student = records.find(
			student => student.id == studentID
		);
		return student.name;
	}
	
})();

Student.getName(73); // Suzy
```