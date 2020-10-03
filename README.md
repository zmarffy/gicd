# `gicd`

`gicd` is a Python decorator that will automatcially create an issue on GitHub if a decorated function throws an exception. That's it!

## Requirements

* The GitHub CLI (`gh`)

## Usage

Decorate a function with it:

```python
from gicd import auto_create_issue

@auto_create_issue(repo_owner="zmarffy", repo_name="cli-test-repo", exceptions=(IndexError, ValueError))
def error_prone_function():
    if input("Don't type anything; just hit enter... "):
        raise ValueError("Explosions!")
    print("All good!")
```

Then call the function:

```python
error_prone_function()
```

On the off chance that the function raises an exception, it will create a issue in the GitHub repo specified in the decorator.

You can have it do this with all exceptions (default behavior), or, if you specify the `exceptions` parameter, it will only create an issue when those specific exceptions are thrown.

There's really not that much else to say about this tiny, somewhat humorous, tool.
