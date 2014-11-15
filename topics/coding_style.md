# Coding Style Best Practices

## Write self-documenting code by doing the following:

1. Avoid abbreviated variable names
  * `discounted_order_total` is a better variable name than something like `dot` or `total_d` 
2. Write out function argument names
3. Document classes and methods
4. Refactor repeated lines of code into reusable functions or methods
  * Don't Repeat Yourself! (DRY)
5. Keep functions and methods short. 
  * They should do one thing (or maybe a couple of things), and should do it well.

## PEP-8

Follow [PEP-8 coding conventions](#) whenever possible and practical. At a minimum:

1. Use 4 spaces (not tabs) per indentation level.
2. Separate top-level function and class definitions with two blank lines.
3. Separate method definitions inside a class with a single blank line

It can be helpful to use a plugin such as 

### Regarding line limits

PEP-8 prescribes a limit of 79 characters per line of code. There is also a prevision for relaxing this limit to 99 characters for projects in which code is not public facing. 

It's 2015, and often feels ridiculous to adhere to arbitrary hardware limits from decades ago. Try to adhere to line limits whenever possible. Sometimes, you can't or would rather not (for example, because you'd rather not sacrifice readability of a variable name). Again, try to keep the line lengths short whenever possible.

## Imports

### Ordering of imports 

According to PEP-8, imports should be grouped in the following order:

1. Standard library imports
2. Related third-party imports
3. Local application or library specific imports

For a Django project, specifically, it's recommended to do:

1. Standard library imports
2. Django core imports
3. Third-Party App imports
4. Local Django Project / App imports

For example:

	# Standard library imports
	from math import sqrt
	from os.path import abspath

	# Core Django imports
	from django.db import models

	# Third-party app imports

	# Local app imports...this can be improved. See section on Relative Imports.
	from myapp.models import MyModel

### Relative imports

Use explicit relative imports, whenever possible. Explicit relative imports can be used when importing from another module **in the current app**.

For example:

    # This explicit relative import of a model
    # from the current app we're in...
    from .models import MyModel

    # Is an improvement over...
    from myapp.models import MyModel

### Avoid using `import *`

Explicitly import each module, rather than using `import *`. This will help prevent naming collisions. An exception is mentioned in the Configuration Files: Settings section of this repository.

    # Avoid this:
    from django.forms import *

    # In favor of this:
    from django import forms

## Additional Considerations

1. Use underscores `_` in url pattern names, but dashes `-` in the actual URLs.