# A bunch of Python scripts to use, enhance and share

## split-yaml

This Python 3 script takes a YAML file with multiple documents (separated by `---`) and writes each of them into a new, separate file.

Use  `split-yaml -h` for a usage overview.

### dependencies

This script requires the [PyYAML](https://pypi.org/project/PyYAML/) library version 5.4.1 or later.
The library can be installed with `pip install pyyaml`, either directly (requires `pip` to be installed) or from within a virtual environment (includes `pip`).

### how to set the filename scheme

The filenames of the newly created files are determined by the value of the key passed to the script.

Let's make an example for better understanding:

Every document in the YAML source file has a key `model:` and you want to use the value of that key for the new fielnames:

Two documents in `source.yaml`:
```yaml
manufacturer: APC
model: ACRC301S
slug: acrc301s
---
manufacturer: APC
model: SMT1000I
slug: smt1000i
```

Calling the script with `split-yaml --file source.yaml --key model` will result in two new files `acrc301s.yaml` and `smt1000i.yaml`.

**important**: Currently, the value of the given key must be unique for every document, otherwise you will overwrite previous files with the same key value.

## tips

If you want to run the scripts from you command line without having to specify the full path, create a symbolic link for each script in a directory that's part of your $PATH, for example:

```zsh
ln -sf <repo path>/split-yaml ~/bin/split-yaml
```

Now, reload/reopen your shell/terminal and you can use `split-yaml` from wherever you are.
