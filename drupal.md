# Drupal

This section is a work in progress!

## Security updates

Our general policy is:

1. Only update contrib modules with security advisories (i.e. do not update all contrib modules to their latest stable release)
2. Submit a pull request with one commit per module updated, to make reviewing changes (and reverting, if need be) easier

When updating sites without test coverage, be especially cautious. When updating contrib modules, always:

1. Review the issue queue for the module and review bug reports that exist for the version being updated to
2. Review the code changes to the module and note if any backwards incompatible API changes have been made

Note that in some cases, the security advisory may not apply to the contributed module as used on the site (i.e. "Only users with `Administer flags` can exploit this vulnerability"), in which case using [Update Advanced](https:/www.drupal.org/project/update_advanced) to ignore the update may be a good option.

## Repository structure

## Drupal root structure

e.g. contrib/custom/patched/features etc directories

settings.php set up, etc

## Theming

### Theme development

Drupal.org's [theming guide](https://www.drupal.org/documentation/theme) is a vast resource for theming best practices and techniques. The guide is split between Drupal 6 & 7, and Drupal 8.

### Best practices

Start by reviewing the theming guide's [best practices section](https://www.drupal.org/node/341707).

#### Keep logic out of template files

In Drupal 6 and 7, PHP logic should mostly exist in `template.php` and feed
prepared variables to template files rather than executing the PHP within the
templates. In Drupal 8 PHP can't be executed in template files at all and must
live in `[theme name].theme`.

#### SMACSS

When creating a custom theme, use [SMACSS](https://smacss.com/) or a
[simplified version](http://savaslabs.com/2015/08/28/sassy-drupal-theming-part-2.html)
for file structure.

#### BEM

Use the BEM methodology for naming CSS classes. CSS Wizardry has a
[great primer.](http://csswizardry.com/2013/01/mindbemding-getting-your-head-round-bem-syntax/)

### Workflow

If possible, it's best to compile CSS files as part of deployment and local
development rather than committing compiled CSS. That said, in certain
development workflows (e.g. Pantheon) it may be necessary to commit compiled CSS
files.
