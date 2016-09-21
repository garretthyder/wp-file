# Wordpress File (wrapper class)

This small class library facilitates file handling for Wordpress custom developments, will provide all functionality to meet Wordpress' standards.

Features:
* **Theme Check** ready.
* Easy to use.

## Installation

### With composer

Make the dependecy required in your project:
```bash
composer require 10quality/wp-file
```

### Alternative

Download or clone the project and load the class with php functions:
```php
require_once '[PATH TO CLASS]/File.php';
```

## Usage

The following example will let you see how to use the class:

Code to replace
```php
$filename = __DIR__.'/myfile.txt';

$file = @fopen( $filename, ,'w+' );

$content = fread( $file );

fwrite( $file, $content );

fclose($file);
```

Replacement:
```php
use TenQuality\WP\File;

$filename = __DIR__.'/myfile.txt';

$content = File::auth()->read( $filename );

File::auth()->write( $filename, $content );
```

### Authentication

Wordpress will require to authenticate a url in order to validate if filesystem credentials are in place.

If you need to authenticate a specific url, pass it like this:

```php
File::auth( $url )->read( $filename );
```

### Folder handling

Methods to handle files:
```php
$file = File::auth();

// Use is_dir to check if a path exists or not.
if ( $file->is_dir( $path ) )
    // Use mkdir to create unexistent paths.
    $file->mkdir( $path );
// Use rmdir to remove paths.
$file->rmdir( $path );
```

### Recomendations

Store your files in the `uploads` folder.