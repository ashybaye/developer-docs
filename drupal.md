# Drupal

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
