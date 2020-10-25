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

```text
error_prone_function()
```

In the off chance that the function raises an exception, it will create a issue in the GitHub repo specified in the decorator.

You can have it do this with all exceptions (default behavior), or, if you specify the `exceptions` parameter, it will only create an issue when those specific exceptions are thrown.

If you want to integrate this info your own app without having to specify the `repo_owner` and `repo_name` keyword arguments in the decorator, you can place a file with a name of your choice in a certain folder, formatted like this example:

```text
zmarffy
cli-test-repo
```

This is a useful file for installers to create, then.

It would make sense for us to call that file `cli-test`, in this example case. You can then use the decorator with only the `app_name` keyword argument, set to the name of the file you created:

```text
@auto_create_issue(app_name="cli-test", exceptions=(IndexError, ValueError))
```

The folder you place it in is:

| OS | Folder |
| --- | --- |
| Linux | `/etc/ghinfo/` |
| Windows | `%PROGRAMDATA%\ghinfo\` |
| macOS | `/Library/Application Support/ghinfo/` |

There's really not that much else to say about this tiny, somewhat humorous, tool.
