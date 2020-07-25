* how to represent a float point number
	* [link](https://www3.ntu.edu.sg/home/ehchua/programming/java/datarepresentation.html)
	```
	The most significant bit is the sign bit (S), with 0 for positive numbers and 1 for negative numbers.
	The following 8 bits represent exponent (E).
	The remaining 23 bits represents fraction (F).
	```
* how to print the type of a class or function
	* using typeid.name() 
	* if there is a virtual fuction, then the pointer to a derived class will be print as devrived class type (*base_pointer_2_devrived) ，refer [link](https://stackoverflow.com/questions/24457350/print-type-of-object-referenced-by-base-class-pointer-in-c)
	```
	nvdsinfer:
	PN8nvinfer117IExecutionContextE //pointer of the base class type
	trtexec:
	N8nvinfer12rt16ExecutionContextE
	```
