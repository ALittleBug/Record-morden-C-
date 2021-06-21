* what's the default value for unordered_map, if the key is not exsist
  ```
  The map's operator[] is specified thus:([map.access])

  Effects: If there is no key equivalent to x in the map, inserts value_type(std::move(x), T()) into the map.
  Returns: A reference to the mapped_type corresponding to x in *this.

  T() uses value-initialisation for all T except void ([expr.type.conv]/2), and value-initialisation for a primitive results in zero-initialization ([dcl.init]/7).

  Therefore, the expression evaluates to a reference to an object with value zero ([dcl.init]/5).

  The operator++ call then increments that object to one, and evaluates to one.
  ```
  * https://stackoverflow.com/questions/2667355/mapint-int-default-values
