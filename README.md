# PHP Renderer

The PHP Renderer is a simple templating engine that allows you to separate the presentation layer from your PHP code. It provides a basic template inheritance mechanism inspired by popular templating engines like Twig.

[![Latest Stable Version](http://poser.pugx.org/devcoder-xyz/php-renderer/v)](https://packagist.org/packages/devcoder-xyz/php-renderer) [![Total Downloads](http://poser.pugx.org/devcoder-xyz/php-renderer/downloads)](https://packagist.org/packages/devcoder-xyz/php-renderer) [![Latest Unstable Version](http://poser.pugx.org/devcoder-xyz/php-renderer/v/unstable)](https://packagist.org/packages/devcoder-xyz/php-renderer) [![License](http://poser.pugx.org/devcoder-xyz/php-renderer/license)](https://packagist.org/packages/devcoder-xyz/php-renderer) [![PHP Version Require](http://poser.pugx.org/devcoder-xyz/php-renderer/require/php)](https://packagist.org/packages/devcoder-xyz/php-renderer)
## Installation

You can install the PHP Renderer library using Composer. Just run the following command:

```bash
composer require devcoder-xyz/php-renderer
```

## Basic Usage

To use the PHP Renderer in your project, first create an instance of the `PhpRenderer` class and pass the directory where your templates are located:

```php
use DevCoder\Renderer\PhpRenderer;

// Specify the template directory
$templateDir = '/path/to/templates';

// Optional parameters to be passed to the templates
$parameters = [
    'siteTitle' => 'My Website',
];

// Create the renderer instance
$renderer = new PhpRenderer($templateDir, $parameters);
```

### Creating Templates

Create your templates using PHP files. For example, create a template file named `template.php` with the following content:

```php
<?php $this->extend('layout.php'); ?>

<?php $this->startBlock('title'); ?>
    My Page Title
<?php $this->endBlock(); ?>

<?php $this->startBlock('content'); ?>
    <h1>Hello, <?php echo $name; ?>!</h1>
    <p>Welcome to my website.</p>
<?php $this->endBlock(); ?>
```

### Creating Layouts

Create a layout file (e.g., `layout.php`) that represents the common structure of your web pages. Use blocks to define sections that will be replaced by content from individual templates.

```php
<!DOCTYPE html>
<html>
<head>
    <title><?php echo $this->block('title'); ?></title>
</head>
<body>
    <div class="container">
        <?php echo $this->block('content'); ?>
    </div>
</body>
</html>
```

### Rendering Templates

To render your templates, use the `render` method of the `PhpRenderer` class:

```php
echo $renderer->render('template.php', ['name' => 'John']);
```

This will render the `template.php` with the provided context data and inject it into the `layout.php` to create the final HTML output.

### Helper Methods

You can use the `get` method to access parameters passed to the renderer:

```php
// Get a parameter value
$siteTitle = $this->get('siteTitle');
```

## Template Inheritance

The PHP Renderer allows you to extend layouts and override specific blocks in child templates. When you use the `extend` method in a template, it tells the renderer to inherit the layout defined in the extended template. You can then use `startBlock` and `endBlock` to override the content of specific blocks in the layout.

## Contributing

Contributions to the PHP Renderer library are welcome! If you find any issues or want to suggest enhancements, feel free to open a GitHub issue or submit a pull request.

## License

The PHP Renderer is open-source software released under the MIT License. See the [LICENSE](LICENSE) file for more details.