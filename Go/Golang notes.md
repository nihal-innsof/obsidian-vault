#### Blank identifier `_`:

The blank identifier in golang is used for various purposes, one of it is to import a package and not use any of its function's, without causing any error's. This can be utilized while importing specific packages, who function's are of no use for us, but we need them for their **side effects**.
_E.g. Importing database package just to use it's side effects for registering a database driver_

** the above given use case is just one of many **

##### What is meant by importing a package not to use them but for their *side effects* mean ?
This means that, just by importing a package will itself cause some code to be executed on app startup putting our system in a different state than it is before importing those packages (like laying down config file's, modifying resources on disc, etc).