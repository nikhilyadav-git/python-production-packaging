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
