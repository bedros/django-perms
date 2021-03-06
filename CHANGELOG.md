# Change Log for django-perms

## 1.4.0 - unreleased

In progress...

## 1.3.0 - 2016-07-27

### Functional Changes

- Added Django REST Framework's request class to the default list of
  expected request types. DRF seems popular enough to warrant this.

### Other Changes

- Added a description of the project to the README.
- Updated the README to document the preferred style of registering
  permissions via an explicitly-created permissions registry.
- Added a new & improved Makefile.
- Added change log file to package manifest.
- Cleaned up change log.
- Added support for Python 3.5.
- Added tox dependency and configuration for testing multiple Python and
  Django version combinations.
- Added Python 3.4 to list of versions to test under Travis CI.
- Added linting when running tests (via flake8).
- Cleaned up some lint found by flake8.
- Fixed a few things, mostly test-related, to support Django 1.9.
- Removed nose and django_nose dependencies; Django's `DiscoverRunner`
  is used to discover and run tests instead.
- Dropped support for Python 2.6.

## 1.2.1 - 2015-05-19

### Fixed

- `PermissionsRegistry._get_user_model()` was unintentionally
  decoratored with `@property`.

## 1.2.0 - 2015-05-15

### Deprecated

- Object-notation access to permissions will be removed in 2.0. All
  views should be decorated using `@permissions.require('perm_name')`
  instead of `@permissions.perm_name`.

### Changed

- Template filters now immediately return False if they're passed
  a non-user object (that is, an object that is not an instance of
  get_user_model() or AnonymousUser). This makes these template filters
  less likely to crash the page.
- Template filters now bypass the call to the permission function for
  anonymous users when anonymous users aren't allowed.

## 1.1.0 - 2015-03-27

### Fixed

- Template filters now bypass the call to the permission function when
  appropriate (e.g., when `allow_staff=True` and the user is staff). The
  logic for this was already in place but was broken due to operator
  precedence.
- Tests now run on Python 2.6.
- Tests no longer cause warnings under Django 1.7 (due to missing
  `MIDDLEWARE_CLASSES` setting).

### Added

- `PermissionsRegistry.entry_for_view(view, permission_name)` can be
  used to whether a view requires a permission. This is intended for use
  in testing.
- Travis CI config was added.

## 1.0.0 - 2015-03-25

Initial version.
