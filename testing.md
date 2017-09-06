# Testing

## Introduction

> Code without tests is broken by design. ([Citation](http://toastdriven.com/blog/2011/apr/10/guide-to-testing-in-django/))

Testing is a critical part of the development process at Savas Labs:

- All projects should have automated tests
- New features added to a codebase should almost always come with tests to verify their functionality
- Bug fixes should almost always contain new tests or fixes to existing tests

Why do we write tests?

- Define the feature you are building or the bug you are fixing
- Improve our code by checking against different assumptions
- Catch regressions
- Help future-you and or co-workers with refactoring
- A green :heavy_check_mark: on your GitHub pull request feels good

## Types of tests

### Linting

The simplest test is PHP linting. Running `php -l {some_directory}` will parse all PHP files and check for syntax errors.

All projects should include a lint check as part of the automated testing process.

### Coding standards

All the custom code we produce must adhere to coding standards. For Drupal projects, this involves running the `phpcs` command with the `--standard=Drupal` option.

Example usage in a Makefile:

``` Makefile
phpcs_config = --ignore=*.css,*.min.js,*features.*.inc,*.svg,*.jpg,*.json,*.woff*,*.ttf,*.md \
--exclude=Drupal.InfoFiles.AutoAddedKeys

phpcs: ##@test Run code standards check.
  docker run --rm -v $$(pwd):/work skilldlabs/docker-phpcs-drupal phpcs --standard=Drupal \
  tests drupal/sites/all/modules/custom $(phpcs_config)
```

All projects should include a coding standards check as part of the automated testing process.

### Behat

All our Drupal projects should incorporate [Behat](http://behat.org/en/latest/) tests, using the [DrupalExtension](https://github.com/jhedstrom/drupalextension) plugin to provide access to the Drupal API from within the Behat testing environment.

We have examples of client projects to draw upon for example configuration of Behat.

#### Use Behat as a communication and discovery tool

Involve the client in defining the scenarios and features. [This page](http://behat.org/en/latest/quick_start.html) contains an excellent overview of how you might do this. You should work with the client to define what the features/scenarios under development are before any code is written.

#### Write the feature/scenario definition before you build the functionality

Following from the above, do not write a Behat feature/scenario _after_ you've coded the implementation. Work with the client to agree on how the feature should work. After you have defined the feature and how it should work in different scenarios, write the code that matches the specification so that the Behat test passes.

#### Prefer human-readable step definitions to reliance on selectors

Consider the following Behat step:

``` cucumber
And I click on the element with XPath '//*[@id="edit-submit"]'
```

While we can read this and infer that `edit-submit` must be referring to the submit button on the page, it is much better to have something like this:

``` cucumber
And I submit the form
```

Then, in your `FeatureContext.php` file, you could implement the code which clicks on the element with the XPath.

The idea is to have a terse description of what the feature should do to provide for a shared understanding between the client and the developer. In this case, the client doesn't need to know about XPath or particular selectors; they will want to know what happens when the form is submitted.

#### Avoid adding too many Behat tests

It is tempting to test everything with Behat. But it's important to counter-balance this with the fact that Behat tests are more difficult to maintain and slower to run than unit tests. Consider whether a unit test is more appropriate before adding a new Behat test.

### Unit

Unit tests should be included on custom development for Drupal 8 projects.

Unit testing vanilla Drupal 7 code is not possible. However, by making use of the the [XAutoload](https://www.drupal.org/project/xautoload) module, one can write object-oriented, unit-testable code.

We use [PHPUnit](http://phpunit.de/) for unit tests.

#### Consider using `phpspec` to design the code needed for a feature

The [phpspec](http://www.phpspec.net/en/stable/) project assists developers in designing the specification for code. Code written using `phpspec` is going to be easier to unit test.

#### Use unit testing in conjunction with Behat tests

Using Behat to capture every permutation of a feature is difficult and costly to implement. It is more efficient to use unit tests to handle testing the different inputs/outputs, and use Behat for a broader overview of the feature.

### Manual

Manual testing should be avoided as the primary means for verifying a feature's functionality, or the correctness of a bug fix. This is because the process is error prone, time consuming, and often tedious. 

That aside, it's good practice in bug reports and pull requests to provide a summary of steps to test a feature or reproduce a bug. Manual verification can help developers and code reviewers confirm that no new, uncaught regressions have occurred. This is also a good opportunity for the code reviewer to step back and assess the feature or fix in the broader context of the project.

## Travis CI

We tie the above together using an automated testing tool called [Travis CI](http://travis-ci.com/).

Because we have standardized our development environments on a combination of Docker, AWS S3 for seed databases, and a Makefile for setup, configuring Travis CI is pretty straightforward, and does not differ in substance from local setup instructions.

All projects with tests should have those tests run on a per branch and/or per pull request basis.
