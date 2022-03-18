## Separate Layers

You can have your layer files defined in the blueprint itself or at the project level. Example:

* **Blueprint Layers**: These layers ship with the blueprint. Think of them as defaults that ship with the blueprint itself. IE: `app/blueprints/demo/config`. These layers are processed first and take lower precedence.
* **Project Layers**: These layers are your project-specific settings. IE: `config/blueprints/demo`. These layers are processed later and take higher precedence. They override previous layer values.

It is recommended to define layers at the project-level, `config/blueprints`. This allow blueprints to be even more reusable.
