Image resize
================

Install
-------

You can install ImageResize by composer. Add this row to your composer.json.

```json
{
    "require": {
        "Innobotics/ImageResize": "1.*"
    }
}
```

But do you want to include this pack use this:

```php
require_once '/path/to/Innobotics/ImageResize.php';
```

Usage
-----

You should create an image object.

```php
$image = new \Innobotics\ImageResize();
```

Add types. The type contains the key, and the image's size.

```php
$image->setType('large', 640, 480);
$image->setType('medium', 320, 240);
$image->setType('thumbnail', 160, 120);
```

Add the source file.

```php
$image->setSource('/home/notesz/teszt/bianka_160117.jpg');
```

Add the target folder.

```php
$image->setTarget('/home/notesz/teszt/resized');
```

If you don't like the original name, you can add a new filename. (It is optional)

```php
$image->setFileName('bianka.jpg'); //optional
```

Would you like to use a file prefix? Add this one: (It is optional)

```php
$image->setPrefix('image'); //optional
```

If you don't want to save the original image you can disable it. Add this one: (It is optional)

```php
$image->setSaveOriginal(false); //optional
```

Resize your image.

```php
if ($image->resize() === true) {
    print 'It\s okay! :)';
} else {
    print 'Something happened!';
}
```
Then you can reach the result.

```php
print_r($image->getResult());
```

If the resize was success, the result is:

```php
Array
(
    [status] => success
    [message] => Array
        (
            [files] => Array
                (
                    [large] => image_bianka_large.jpg
                    [medium] => image_bianka_medium.jpg
                    [thumbnail] => image_bianka_thumbnail.jpg
                    [original] => image_bianka.jpg
                )

        )

)
```

But the resize was false, the result is:

```php
Array
(
    [status] => error
    [message] => unable to open image `/home/notesz/teszt/IMG_790s7.jpg': No such file or directory @ error/blob.c/OpenBlob/2638
)
```
