Choosing a Framework
====================

Protractor supports three behavior driven development (BDD) test frameworks: Jasmine, Mocha, and Cucumber. These frameworks are based on JavaScript and Node.js and provide the syntax, scaffolding, and reporting tools you will use to write and manage your tests.


Using Jasmine
-------------

Currently, Jasmine Version 2.x is supported and the default test framework when you install Protractor. For more information about Jasmine, see the [Jasmine GitHub site](http://jasmine.github.io/). For more information regarding how to upgrade to Jasmine 2.x from 1.3, see the [Jasmine upgrade guide](/docs/jasmine-upgrade.md).


Using Mocha
-----------

_Note: Limited support for Mocha is available as of December 2013. For more information, see the [Mocha documentation site](http://mochajs.org/)._

If you would like to use the Mocha test framework, you'll need to use the BDD interface and Chai assertions with [Chai As Promised](http://chaijs.com/plugins/chai-as-promised).

Download the dependencies with npm. Mocha should be installed in the same place as Protractor - so if protractor was installed globally, install Mocha with -g.

```
npm install -g mocha
npm install chai
npm install chai-as-promised
```

You will need to require and set up Chai inside your test files:

```js
var chai = require('chai');
var chaiAsPromised = require('chai-as-promised');

chai.use(chaiAsPromised);
var expect = chai.expect;
```

You can then use Chai As Promised as such:

```js
expect(myElement.getText()).to.eventually.equal('some text');
```

Finally, set the 'framework' property to 'mocha', either by adding `framework: 'mocha'` to the config file or by adding `--framework=mocha` to the command line.

Options for Mocha such as 'reporter' and 'slow' can be given in the [config file](../spec/mochaConf.js) with mochaOpts:

```js
mochaOpts: {
  reporter: "spec",
  slow: 3000
}
```

For a full example, see Protractor’s own test: [/spec/mocha/lib_spec.js](/spec/mocha/lib_spec.js).


Using Cucumber
--------------

_Note: Limited support for Cucumber is available as of January 2015. Support for Cucumber in Protractor is maintained by the community, so bug fixes may be slow. For more information, see the [Cucumber GitHub site](https://github.com/cucumber/cucumber-js)._


If you would  like to use the Cucumber test framework, download the dependencies with npm. Cucumber should be installed in the same place as Protractor - so if protractor was installed globally, install Cucumber with -g.

```
npm install -g cucumber
```

Set the 'framework' property to cucumber, either by adding `framework: 'cucumber'` to the [config file](../spec/cucumberConf.js) or by adding `--framework=cucumber` to the command line.

Options for Cucumber such as 'format' can be given in the config file with cucumberOpts:

```js
cucumberOpts: {
  format: "summary"
}
```

For a full example, see Protractor’s own test: [/spec/cucumber/lib.feature](/spec/cucumber/lib.feature).


Using a Custom Framework
------------------------

Check section [Framework Adapters for Protractor](../lib/frameworks/README.md) specifically [Custom Frameworks](../lib/frameworks/README.md#custom-frameworks)


