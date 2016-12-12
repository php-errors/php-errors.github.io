## Overview

This open source organization is an attempt to bring the PHP community together,
to design and ratify standardized methods for handling errors in PHP.

This website contains details of the relevant specifications and software
packages published by this organization, as well as instructions for how to
integrate them into your projects.

## Packages

### Error handling packages

A number of [Composer] packages exist, that are designed to aid in integrating
standardized error handling into your projects. These packages serve three main
purposes:

- To clearly define the error handling requirements of the project.
- To highlight any conflicting error handling requirements of different packages
  utilized by the project, and its dependencies.
- To automatically install an appropriate error handler for the project.

[composer]: https://getcomposer.org/

#### Usage of the error handling packages

To utilize an error handling package, simply choose the package that best
describes the error handling requirements of your project from the options
detailed below, and include that package in your project's requirements using
`composer require`.

So long as the dependencies of your project also specify their error handling
requirements using the same set of packages, you will be warned about any
conflicting requirements by Composer.

#### The `errors/exceptions` package

Adding this package as a dependency indicates that the root package is designed
to work with exception-based error handling as described in the
[exception-based error handler specification][exception-based-error-handler],
and will *not* work correctly with the "native" errors that PHP produces by
default:

    composer require errors/exceptions

This package installs an exception-based error handler upon installation. It is
not necessary to manually install the error handler via [set_error_handler()].

See also, the [repository page][exceptions-repo] for this package.

[exceptions-repo]: https://github.com/php-errors/exceptions
[set_error_handler()]: https://php.net/set_error_handler

#### The `errors/native` meta-package

Adding this package as a dependency indicates that the root package is designed
to work with "native" errors that PHP produces by default, and will *not* work
correctly with exception-based error handlers, such as the one described in the
[exception-based error handler specification][exception-based-error-handler]:

    composer require errors/native

This package is a meta-package. It does not include any code, but rather, exists
solely to conflict with the `errors/exceptions` package.

See also, the [repository page][native-repo] for this package.

[native-repo]: https://github.com/php-errors/native

#### The `errors/any` meta-package

Adding this package as a dependency indicates that the root package is designed
to work with exception-based error handlers, such as the one described in the
[exception-based error handler specification][exception-based-error-handler],
but that it also supports "native" errors that PHP produces by default:

    composer require errors/any

This package is a meta-package. It does not include any code, but rather, exists
solely so that projects may indicate that they are flexible in their error
handling requirements.

See also, the [repository page][any-repo] for this package.

[any-repo]: https://github.com/php-errors/any

### Other packages

#### The `errors/specification` package

This repository contains specification documents, and associated testing tools
for ensuring conformance. It can be included as a development-only dependency in
order to test conformance of custom implementations to the specifications
published by this organization:

    composer require --dev errors/specification

See also, the [repository page][specification-repo] for this package.

[specification-repo]: https://github.com/php-errors/specification

## Specifications

At the current time, there is only one published specification: an
exception-based error handler. More specifications will be published as
required.

### Exception-based error handler

This specification describes a standardized method for handling errors in PHP,
by converting the errors into thrown [ErrorException] exceptions. See the full
specification [here][exception-based-error-handler].

[errorexception]: https://php.net/errorexception
[exception-based-error-handler]: https://github.com/php-errors/specification/blob/master/exception-based-error-handler.md

## Contributing

To report an issue, or ask a question, please submit an issue, or pull request,
to the most appropriate repository under the
[php-errors organization on GitHub].

[php-errors organization on github]: https://github.com/php-errors
