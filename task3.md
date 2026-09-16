Having `Board3D` extend `Board` is a bad design choice.
- **S**: 
- **O**: It violates the Open/Closed prinicple, as `Board` would have to be significantly modified in order to accomodate being inherited by `Board3D`.
- **L**: It violates the Liskov Substitution Principle; that is, if `Board3D` extends `Board`, then `Board3D` should be usable anywhere a `Board` is expected. However, `Board3D`'s `setLocation()` method would have to require 3 coordinates, not the 2 coordinates that its superclass would accept, and so when a `Board` is given a `Board3D`, it could break.
- **I**: 
- **D**:

The behavior of a 3D board is simply too different from that of a 2D board to justify a 3D board being a specialization of a 2D.