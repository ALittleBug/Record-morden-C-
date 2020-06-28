[avoid reference member](https://stackoverflow.com/questions/892133/should-i-prefer-pointers-or-references-in-member-data)
```
Avoid reference members, because they restrict what the implementation of a class can do 
(including, as you mention, preventing the implementation of an assignment operator)
and provide no benefits to what the class can provide.
```
