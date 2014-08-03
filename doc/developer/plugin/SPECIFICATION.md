Plugin Specification 0.1.0
==========================

As a plugin, your code needs to conform to these specifications so that the Shim bootstrap layer can use it.

File System
-----------

Your plugin's folder structure must contain the following files and paths (* indicates optional file):

> bootstrap.js
> npm-shrinkwrap.json *
> package.json
> README.md *

Any dependencies will be resolved via the package.json when invoked by the plugin bootstrap process.

Bootstrap Entry Point
---------------------

The bootstrap.js defines the methods and resources available to the Shim bootstrap loader.  It is structured as follows:

> exports.api = {
>   OPTIONS: {
>     GET: {
>       exampleResource1: function() { 
>         // Implement GET functionality for example resource 1
>       },
>       exampleResource2: function() { 
>         // Implement GET functionality for example resource 2
>       }
>     },
>     POST: {
>       exampleResource1: function() {
>         // Implement POST functionality for example resource 1
>       }
>     },
>     DELETE: {
>       exampleResource1: function() {
>         // Implement DELETE functionality for example resource 1
>       }
>     }
>     // etc...
>   }
> }

Response Objects
----------------

Every resource function MUST return a JSON object with the following data:

{
  "status": "[HTTP status code indicating success or failure]",
  "header": "[Raw header content]",
  "body": "[Raw body content]",
  "resource": {
	"field1": value,
	"field2": value,
	etc...
  }
}

The Shim REST layer will validate the response data and return an error to the client if this structure is not adhered to.

Changelog
---------

0.1.0 Defined Initial Specification