# Python Buildpack Binaries


To get started with it, create an app on Heroku inside a clone of this repository, and set your S3 config vars:

    $ heroku create --buildpack https://github.com/heroku/heroku-buildpack-python
    $ heroku config:set AWS_ACCESS_KEY_ID=<your_aws_key>
    $ heroku config:set AWS_SECRET_ACCESS_KEY=<your_aws_secret>
    $ heroku config:set S3_BUCKET=<your_s3_bucket_name>


Then, shell into an instance and run a build by giving the name of the formula inside `builds`:

    $ heroku run bash
    Running `bash` attached to terminal... up, run.6880
    ~ $ bob deploy --overwrite runtimes/python-2.7.12
    ~ $ bob deploy --overwrite libraries/vendor/openldap
    ~ $ bob deploy --overwrite libraries/vendor/sasl
    ~ $ bob deploy --overwrite libraries/vendor/wkhtmltopdf

If this works, run `bob deploy` instead of `bob build` to have the result uploaded to S3 for you.

To speed things up drastically, it'll usually be a good idea to `heroku run bash --size PX` instead.

Enjoy :)
