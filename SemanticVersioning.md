# Semantic Versioning
- https://semver.org/
- MAJOR.MINOR.PATCH
- MAJOR
    - breaking change, backward incompatible
    - 2.0.0, 2.0.1, ...
- MINOR
    - adding new functionality/feature, backward compatible
    - 1.1.0, 1.1.1, ...
- PATCH
    - no new functtionality, bug fixes, performance optimization
    - 1.0.0, 1.0.1, ...
- Example - package [add_library.py]
    - 0.0.1 - When to use 0.0.1?
        - You’ve just started a project.
        - It’s not production-ready.
        - You're setting up the base structure (e.g., a basic API route, function, or CLI command).
        - You're signaling to others: "This is a work in progress. Don't rely on it for stability yet."
        -  So to summarize 
            - MAJOR = 0 → The software/library is still in initial development. Anything can change at any time. There is no guarantee of backward compatibility.
            - MINOR = 0 → No new features yet.
            - PATCH = 1 → The very first working version, typically with basic functionality.
    - 1.0.0 -> 1.1.0: Minor update (non-breaking): Added new optional parameter d.
    - 1.1.0 -> 2.0.0: Major update (breaking): Made d a required parameter, which breaks compatibility with previous versions.
    - pip install add_library=1.0.0 or pip install add_library<=2 should be fine but pip install add_library=2.0.0 will intoduce breaking changes
    ```python
    # Version 1.0.0
    # Initial version: function supports adding 3 numbers
    def add_numbers(a, b, c):
        return a + b + c

    # Version 1.1.0
    # Non-breaking change: added support for an optional 4th number.
    # Backward compatible as 'd' defaults to 0 if not provided.
    # new functionality to add new method to support sunstraction
    def add_numbers(a, b, c, d=0):
        return a + b + c + d

    def subtract_numbers(a, b):
        return a - b

    # Version 2.0.0
    # Breaking change: 'd' is now a required parameter.
    # This breaks backward compatibility with any code calling the function with only 3 arguments.
    def add_numbers(a, b, c, d):
        print("""WARNING - 
        add_number function will be deprecated in future release!
        Use sum() instead!!
        """)
        return a + b + c + d

    # Version 3.0.0
    # Breaking change: changed method name
    # This breaks backward compatibility with any code calling the function with add_numbers should call with with sum.
    def sum(a, b, c, d):
        return a + b + c + d
    ``` 
- Real World Examples
    - __PATCH__ - "1.1.2" because the addition of type hints is considered a minor update rather than a change in functionality, making it suitable for a patch version. This aligns with semantic versioning, where such adjustments enhance usability without altering existing capabilities.
        ```python
        # old version: 1.1.1
        class DataObject:
            def __init__(self, columns, name):
                self.name = name
                # the double underscore means this attribute is private
                self.__columns = columns
    
        # new version: 1.1.2
        class DataObject:
            def __init__(self, columns: list[str], name: str):
                self.name = name
                self.__columns = columns
        ```
    - __PATCH__ - "1.1.2" because the users are meant to access private attributes of objects. Python use 'name mangling' on attributes starting with **double** underscores to prevent user from accessing the attributes altogaher. **single** underscore communicate that author reserves the right to remove that property at any time ithout considering it as backward incompatiable aka majaor change. A single underscroe says 'use this property at your won risk'
        ```python
        # old version: 1.1.1
        class DataObject:
            def __init__(self, columns, name):
                self.name = name
                # the single underscore means this attribute is private
                self._columns = columns
        
        # new version: 1.1.2
        class DataObject:
            def __init__(self, columns, name):
                self.name = name
        ```
    - __MAJOR__ - 2.0.0" because renaming the class means that existing users must change their code, which breaks compatibility; thus, it qualifies as a major version change in semantic versioning. Understanding this concept is crucial, as it highlights the importance of maintaining user code functionality with changes in your project.
        ```python
        # old version: 1.1.1
        class DataObject:
            def __init__(self, columns, name):
                self.name = name
                # the single underscore means this attribute is private
                self._columns = columns
        
        # new version: 2.0.0
        class DataFrame:
            def __init__(self, columns: list[str], name: str):
                self.name = name
                self._columns = columns
        ```
    - __MAJOR__ - "2.0.0" because adding the required fpath parameter changes the __init__() method's signature, breaking existing code that relies on the previous version; this qualifies as a major version change in semantic versioning. This understanding reinforces the importance of maintaining compatibility in your code.
        ```python
        # old version: 1.1.1
        class DataObject:
            def __init__(self, columns, name):
                self.name = name
                # the single underscore means this attribute is private
                self._columns = columns
        
        # new version: 2.0.0
        from pathlib import Path
        from typing import Union
        
        class DataObject:
            def __init__(
                self, 
                columns: list[str], 
                name: str, 
                fpath: Union[str, Path],
            ):
                self.name = name
                self.fpath = fpath
                self._columns = columns
        ```
    - __MINOR__ - "1.2.0" because adding the new fpath parameter with a default value is a minor version change; it enhances functionality without breaking existing code. This demonstrates your understanding of how default parameters can allow for new features while maintaining compatibility, which is a core principle of semantic versioning.
        ```python
        # old version: 1.1.1
        class DataObject:
            def __init__(self, columns, name):
                self.name = name
                # the double underscore means this attribute is private
                self.__columns = columns
        
        # new version: 1.2.0
        from pathlib import Path
        from typing import Union, Optional
        
        class DataObject:
            def __init__(self, columns: list[str], name: str, fpath: Optional[Union[str, Path]] = None):
                self.name = name
                self.fpath = fpath
                self.__columns = columns
        ```

