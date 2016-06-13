# Shakespeare SASS

## About

Shakepeare SASS is a package to enable the usage of [SASS language](http://sass-lang.com)
in the [Yesod web framework](http://yesodweb.com).

## Using Shakespeare SASS

Adding SASS support to your Yesod website is, actually,
quite simple and straight-forward.
After adding `shakespeare-sass` into your `.cabal` file
(and `stack.yaml` if you are using stack),
all you have to do is change your `widgetFileSettings` in `Settings.hs`
from `= def` to `= wfsSass ["sass_include/"]`.
And, of course, `import Text.Shakespeare.Sass` at the beginning of the file.

The argument for `wfsSass` function is a list of directories relative to
the project root where you want
your `.sass` or `.scss` include files stored.
The main SASS files will still reside in your `templates` directory,
as it is with the default setup with `.lucius` files.
That way you get to keep your mixins separate from the templates
and have a clear directory structure.
Of course, you can always add your `templates` directory
to sass search path and keep everything in `templates` dir.

### Note about deployment with Keter

In case you are using [Keter](https://github.com/snoyberg/keter) for deployment
(and you should, it's a great tool),
you should also add directories with your sass templates
to the `extraFiles:` list in the `config/keter.yaml` file.
Don't forget to put the `../` prefix, since `keter.yaml`'s paths are
relative to the `config` directory.
