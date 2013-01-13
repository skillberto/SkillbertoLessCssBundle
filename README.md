LessJsBundle
===================

This Bundle initialize Less.js into Symfony2 Framework

===================
Setup:

//app/AppKernel.php:
...
new Less\CssBundle\LessCssBundle()
...


After that use Symfony2 assets, to put resource into web/bundles directory

Run in console:
php app/console.php assets:install
