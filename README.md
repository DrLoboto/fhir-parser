Python FHIR Parser
==================

A Python FHIR specification parser for model class generation.
The `generate.py` script downloads the latest [FHIR specification][fhir], parses resources and their search parameters and puts them into Python dictionaries.
These dictionaries are then used by [Jinja][] templates to create classes in certain programming languages, mentioned below.

This script does its job for the most part, but it doesn't yet handle all FHIR pecularities and there's no guarantee the output is correct or complete.

### Use ###

1. Copy the file `settings.py` from the respective subdirectory into the project's root directory, 
2. Adjust settings, if necessary
3. Execute `./generate.py` to run the script.
    This will use Python _3_, issue `python generate.py` if you don't have Python 3 yet.
    Supply the `-f` flag to force a re-download of the spec.

> NOTE that the script currently overwrites existing files without asking and without regret.


Languages
=========

This repo currently supports class generation in the following languages:

Swift
-----

[Swift][], Apple's new programming language for OS X and iOS.
Since the language is still under active development, the repo will be updated when a language change occurrs.
The current supported "version" corresponds to what's accepted by Xcode 6 GM.

Python
------

Classes for Python are targeted towards Python 3 but will support the later 2.x versions – at least they should.
All resource classes will inherit from the `FHIRResource` base class, which is a subclass of `FHIRElement`.
Dates are expressed as `FHIRDate` instances which can parse valid ISO dates.

### Todo: ###

```text
[x] Generate Python classes
[x] Deserialize from JSON
[ ] Implement reference resolver (FHIRElement._resolveReference() and co.)
[ ] Generate factories if needed
[ ] Serialize to JSON
[~] Create a FHIR server class/protocol for easy resource hookup
[x] Generate search parameter builder
[x] Generate unit tests from JSON example files
```

### Requirements ###

```text
isodate
```


[fhir]: http://www.hl7.org/implement/standards/fhir/
[jinja]: http://jinja.pocoo.org
[swift]: https://developer.apple.com/swift/