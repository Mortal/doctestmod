## Run doctest on module containing relative import

When running `doctest` on a module that performs a relative import in a PEP-420
namespace package, you get an ugly error saying

```
Parent module '' not loaded, cannot perform relative import
```

This program imports the module using `importlib` and runs `doctest.testmod` on
that to resolve this problem.

You may specify either a dot-separated module path or a filename relative to
the current directory.

If you specify a filename like `foo/bar/baz.py`, this program will add the
current working directory to `PYTHONPATH` and import `foo.bar.baz`.
If instead you specify `foo.bar.baz` directly, `PYTHONPATH` is not modified.
