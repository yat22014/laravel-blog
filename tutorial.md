Deployment notes
1. add Procfile to solve 403 forbidden
web: vendor/bin/heroku-php-apache2 public/

2. cant run npm in heroku
$ heroku config:add BUILDPACK_URL=https://github.com/heroku/heroku-buildpack-nodejs
$ git commit -am "empty" --allow-empty
$ git push heroku master

3. force https assets
To fix that you need to add \URL::forceScheme('https') into your AppServiceProvider file.
    public function boot()
    {
        if(config('app.env') === 'production') {
            \URL::forceScheme('https');
        }
    }