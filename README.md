Symfony2HipayLib
================

This is a package who contains libraries of the payment method Hipay. This is for use in a Symfony2 Application.
It's not a bundle with method, just the libraries of Hipay ready to use in Symfony2.


How to use ?

Install with composer :

"require": {
  "djoo/symfony2hipaylib": "*"
}


Configure your app/autoload.php

<?php

use Doctrine\Common\Annotations\AnnotationRegistry;

$loader = include __DIR__.'/../vendor/autoload.php';

// intl
if (!function_exists('intl_get_error_code')) {
    require_once __DIR__.'/../vendor/symfony/symfony/src/Symfony/Component/Locale/Resources/stubs/functions.php';

    $loader
    ->add('', __DIR__.'/../vendor/symfony/symfony/src/Symfony/Component/Locale/Resources/stubs')
    ->add('HIPAY', __DIR__.'/../vendor/djoo/symfony2hipaylib/lib/hipay') //Add This line
    ;
}


AnnotationRegistry::registerLoader(array($loader, 'loadClass'));

require __DIR__.'/../vendor/djoo/symfony2hipaylib/lib/hipay/mapi_package.php'; //Add This line

return $loader;



And after in your controller you can use the method developped by Hipay.
Don't forget to use this at the top of your controller :
use HIPAY;

And if you need to call method of Hipay can use this for example :
$params = new \HIPAY_MAPI_PaymentParams();

Idem for static method :
$output = \HIPAY_MAPI_SEND_XML::sendXML($xmlTx,$urlHipay);



