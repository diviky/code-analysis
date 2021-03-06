## Goal

Configuration for [grumphp](https://github.com/phpro/grumphp) that is checking on each commit that the committed code passes the unit tests, complies with the PSR2 coding style and static analysis check. It runs the following checks:

-   Check that composer.json is valid
-   Check that composer does not have any dependencies for known security vulnerabilities with [SensioLabs Security Checker](https://github.com/sensiolabs/security-checker)
-   Check that commit does not contain any debugging (var_dump, die, exit)
-   Check that code complies with the PSR2 coding style
-   Perform static code analysis using [phpstan](https://github.com/phpstan/phpstan)
-   Check code for unnecessary complexity etc. with [PHP Mess Detector](https://github.com/phpmd/phpmd)
-   Check that unit tests pass with PHPUnit

## Installation

### 1. Add checker to your `composer.json`:

```
composer require --dev diviky/code-analysis
```

### 2. Add path to grumphp configuration file to your `composer.json`'s extra:

```
    "extra": {
        "grumphp": {
            "config-default-path": "vendor/diviky/code-analysis/grumphp.yml"
        }
    }
```

## Test suites

If you want to run the coding style or static analysis checks only, you can run the following commands:

```
php artisan self-diagnosis

composer validate

vendor/bin/grumphp run --testsuite=style
vendor/bin/grumphp run --testsuite=static
vendor/bin/php-cs-fixer fix --allow-risky=yes
vendor/bin/psalm
vendor/bin/phpstan analyse src
vendor/bin/testbench package:test --parallel
vendor/bin/phpunit --coverage-html coverage

```

## License

The MIT License (MIT). Please see [License File](LICENSE) for more information.
