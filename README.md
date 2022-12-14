# generator-nestjs-fabiano [![NPM version][npm-image]][npm-url] [![Build Status][travis-image]][travis-url] [![Dependency Status][daviddm-image]][daviddm-url]
> Gererates a application based on framework Nestjs v9

## Installation

First, install [Yeoman](http://yeoman.io) and generator-nestjs-fabiano using [npm](https://www.npmjs.com/) (we assume you have pre-installed [node.js](https://nodejs.org/)).

```bash
npm install -g yo
npm install -g generator-nestjs-fabiano
```

Then generate your new project:

```bash
yo nestjs-fabiano
```

## Getting To Know Yeoman

 * Yeoman has a heart of gold.
 * Yeoman is a person with feelings and opinions, but is very easy to work with.
 * Yeoman can be too opinionated at times but is easily convinced not to be.
 * Feel free to [learn more about Yeoman](http://yeoman.io/).

## License

AGPL-3.0 © [Fabiano Nascimento]()


[npm-image]: https://badge.fury.io/js/generator-nestjs-fabiano.svg
[npm-url]: https://npmjs.org/package/generator-nestjs-fabiano
[travis-image]: https://travis-ci.com/fabianorodrigo/generator-nestjs-fabiano.svg?branch=master
[travis-url]: https://travis-ci.com/fabianorodrigo/generator-nestjs-fabiano
[daviddm-image]: https://david-dm.org/fabianorodrigo/generator-nestjs-fabiano.svg?theme=shields.io
[daviddm-url]: https://david-dm.org/fabianorodrigo/generator-nestjs-fabiano

## Maintenance 

### Folder tree

Yeoman’s functionality is dependent on how you structure your directory tree. Each sub-generator is contained within its own folder.

The default generator used when you call yo name is the `app` generator. This must be contained within the `app/` directory.

Sub-generators, used when you call `yo name:subcommand`, are stored in folders named exactly like the sub command. In an example project, a directory tree could look like this:

```
├───package.json
└───generators/
    ├───app/
    │   └───index.js
    └───router/
        └───index.js
```

This generator will expose `yo name` and `yo name:router` commands.


## Extending Generator

Yeoman offers a base generator which you can extend to implement your own behavior. This base generator will add most of the functionalities you’d expect to ease your task. In the generator’s index.js file, here’s how you extend the base generator:

```javascript
const Generator = require('yeoman-generator');

module.exports = class extends Generator {};
```

Some generator methods can only be called inside the constructor function. These special methods may do things like set up important state controls and may not function outside of the constructor. To override the generator constructor, add a constructor method like so:

```javascript
module.exports = class extends Generator {
  // The name `constructor` is important here
  constructor(args, opts) {
    // Calling the super constructor is important so our generator is correctly set up
    super(args, opts);

    // Next, add your custom code
    this.option('babel'); // This method adds support for a `--babel` flag
  }
};
```

Each method directly attached to a Generator prototype is considered to be a task. Each task is run in sequence by the Yeoman environment run loop. In other words, EVERY METHOD added to the prototype is run once the generator is called–and usually in sequence. Each function on the object returned by `Object.getPrototypeOf(Generator)` will be automatically run.

If you have a helper method that shouldn't be called automatically by Yeoman, you can:

- Prefix method name by an underscore (eg. _my_helper_method)
- Use instance methods (eg. this.helperMethod = function() {...})
- Extends a parent generator (create a class that extends Generator and another class to extends the first and will implement the helper method)

However, some special method names will trigger a specific run order. Yeoman has a queue system with priority support, it's called "run loop". Priorities are defined in your code as special prototype method names. When a method name is the same as a priority name, the run loop pushes the method into this special queue. If the method name doesn’t match a priority, it is pushed in the default group.

The available priorities are (in running order):

1. initializing - Your initialization methods (checking current project state, getting configs, etc)
2. prompting - Where you prompt users for options (where you’d call this.prompt())
3. configuring - Saving configurations and configure the project (creating .editorconfig files and other metadata files)
4. default - If the method name doesn’t match a priority, it will be pushed to this group.
5. writing - Where you write the generator specific files (routes, controllers, etc)
6. conflicts - Where conflicts are handled (used internally)
7. install - Where installations are run (npm, bower)
8. end - Called last, cleanup, say good bye, etc


### Creating a subgenerator

Once installed Yeoman itself and it's the generator-generator, run:

```bash
yo generator:subgenerator <subgenerator name>
```
