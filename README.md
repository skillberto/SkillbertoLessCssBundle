LessJsBundle
===================

This Bundle initialize Less.js into Symfony2 Framework

===================
#Setup:

//app/AppKernel.php:<br/>
...
new Less\CssBundle\LessCssBundle()<br/>
...


After that use Symfony2 assets, to put resource into web/bundles directory

#Run in console:

php app/console.php assets:install


#Use the less css JavaScript:

\<script src="{{ asset('bundles/lesscss/js/less-1.3.3.min.js') }}">\</script>

