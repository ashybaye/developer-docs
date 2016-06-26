# Audits

When Savas Labs receives a work-in-progress project, we will review critical functionality, architecture, security, and code pre-development to ensure any risks are identified up front. Some of these items may be optional on certain projects but all are recommended when relevant.

## Goals of site audits

- Identify risks so we can mitigate their impact
- Prepare ourselves for more accurate estimation
- Vet assumptions made by us and our clients
- Accurately quantify the amount of work remaining on the project
- Inform client of how much work previous developers have completed and any issues that have arisen
- Engender trust by showing clients we’re competent, open, and transparent and guide them to a better, less risky, more informed place

## Audit Checklist

### General Security

- Run the [Hacked](https://www.drupal.org/project/hacked) module on the codebase to identify any patched code
- Run [Security Review](https://www.drupal.org/project/security_review) and [Site Audit](https://www.drupal.org/project/site_audit) on site
- For Drupal 7 sites, run [Drupalgeddon](https://www.drupal.org/project/drupalgeddon)

### Hosting

- Check server file permissions
- Find out who can access the server
- Find out how is code deployed
- Check [file and directory permissions](https://www.drupal.org/node/244924)
- Check for server software patches/updates

### Codebase

#### General

- Core and contrib modules are up to date with latest stable release
- Patches, if any, are documented and in a `/patches` directory
- Contrib/custom code is split into (sites/all)/modules/contrib and (sites/all)/modules/custom
- Credentials are not stored in version control
- Modules and themes live in proper place in Drupal

#### Custom code

- Format code for Drupal coding standards
- Run code through [phpcs](https://github.com/FloeDesignTechnologies/phpcs-security-audit)
- Ensure each custom module has a README explaining what it does
- Theme: review templates to ensure output is sanitized

#### Automated tests

- Review existing tests, if any
- If there are not any tests, ask the client to explain what the most important tasks are on the site

### Database

- PHP error settings - Errors go to logs only, not to screen
- Permissions/roles (Security Review module will also help identify issues here)
- Use [Schema module](https://www.drupal.org/project/schema) to identify any mismatched schemas, as well as custom tables that are not part of any module schema

### Functionality of critical site features

Examples:

- eCommerce
- Mail setup

### Useful Tests

- [LinkChecker](https://www.drupal.org/project/linkchecker)
- [WAVE](http://wave.webaim.org/)
- [Mobile friendly test](https://www.google.com/webmasters/tools/mobile-friendly/)
