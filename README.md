# Heroku ruby buildpack and assets in specific path

Although most developer will let heroku handle compiling their assets there are some use cases when precompiling your assets locally make sense.

By defaul the heroku buildpack for ruby checks in the  **public/assets** direcotry for a manifest. If a manifest is found it is assumed that assets are already compiled and this step of [compile step](https://github.com/heroku/heroku-buildpack-ruby/blob/master/lib/language_pack/rails4.rb#L72) is skipped.

With the default rails settings this works out of the box. However if you set the *config.assets.prefix* settings as described in the [Rails documentation](http://guides.rubyonrails.org/asset_pipeline.html#precompiling-assets) this stops working.

The build pack only check in the **public/assets** directory so if the manifest is saved in an other directory it will not be detected and thus assets will be compiled during deploy.

