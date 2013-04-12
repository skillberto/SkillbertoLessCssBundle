# LessJsBundle
===================

This Bundle initialize Less.js into Symfony2 Framework

===================
### Setup:

`app/AppKernel.php`:
```
...
new Less\CssBundle\LessCssBundle()
...
```

### Run in console:
```
assets:install
assetic:dump
```

### Use the less css JavaScript:

```
<script src="{{ asset('bundles/lesscss/js/less-1.3.3.min.js') }}"></script>
```
OR (from bundle)
```
{% javascripts
    '@LessCssBundle/Resources/public/js/*'
 %}
    <script src="{{ asset_url }}"></script>
{% endjavascripts %}
```

With this mode, you can include your .less, eg: style.less 'css':
```
<link rel="stylesheet/less" href="{{ asset('YOURBUNDLE/css/style.less') }}" />
```
But this mode is <b>not secure</b>. Better way to copy into `web/css/` and include from this folder, or use next way.

# Next way: Assetic filter method

For this, you have to use Node, or some kind of PHP or other script.

### With Node:

```
#...
assetic:
    filters:
        cssrewrite: ~
        less:
            node: /usr/local/bin/node
            node_paths: [/usr/local/lib/node_modules]
            apply_to: "\.less$"
...
```

### With PHP:
For example, good way the `leafo/lessphp`:

Put into composer.json:
```
...
"require": {
    ...
    "leafo/lessphp": "0.3.*@dev"
}
...
```

Update composer, and put into `app/config/config.yml`:

```
#...
assetic:
    #...
    filters:
        lessphp:
            file: %kernel.root_dir%/../vendor/leafo/lessphp/lessc.inc.php
            apply_to: "\.less$"
```


Now, you can use from the hood with assetic filter:
```
{% stylesheets 'path/to/files.less' %}
  <link rel="stylesheet" href="{{ assets_url }}" />
{% endstylesheets %} 
```

You can find this documentation, and some kind of other in this url:<br/>
http://dividebyze.ro/178/how-to-use-less-css-and-symfony-2-in-harmony/
