
### bx-setup

`bx-setup` is a BoxLang class designed to simplify module management for your projects. Just add the modules your project needs to a `requirements.txt` file, then run:

```bash
boxlang setup.bx
```

The script will automatically check for missing modules and install them for you.

You can specify modules by name to get the latest version, or include a version to install a specific one:

```text
bx-jsoup
bx-markdown@1.0.0
bx-yaml
```

This makes it easy to keep your project's dependencies up to date and ensures all required modules are available.
