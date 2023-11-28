# Collections
* Dynamic size
* Can assign keys to the content inside the collections, for faster retrieval.
* Collection is a class, so to use them we have to instantiate and use its instance for adding elements etc...
* If the collection we want to use only one data type, then use classes from the namespace `System.Collections.Generic`, they are called generic collections. By using a generic collection where it is needed, we can enforce type safety. 
# Model Binding
It is the process of automatic mapping of data from request's to object's in asp.net core.

# Scaffolding Controllers
This means auto generating controller's based on `model`'s and their associated `database context`
```powershell
dotnet aspnet-codegenerator controller -name TodoItemsController -async -m TodoItem -dc TodoContext -outDir Controllers
```
**`dotnet aspnet-codegenerator controller`** - This tells that the code generator is used to generate a controller
**`-name TodoItemsController`** - This defines the name of the controller class to be generated
**`-async`** - 
**`-m TodoItem`** - Tells the model which the controller should be based of
**`-dc TodoContext`** - Tells the `database context` which the controller should be based of
**`-outDir Controllers`** - Tells the dir where the generated file should be placed