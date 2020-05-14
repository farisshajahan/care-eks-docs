# Production Environment Variables

This section covers the environment and its required setup for running the care project in production. This involves setting up the secret keys, encryption keys, PostGIS database URLs etc. The project also employs other services such as Redis for caching and Sentry for logging.

The following list contains variables you will need during the production environment.

* `POSTGIS_URL`  
__Required__  
This variable is the URL to your Postgres database with the PostGIS extension. To obtain this, simply replace `postgres://` with `postgis://` in your `DATABASE_URL`
* `DJANGO_ADMIN_URL`  
__Required__  
This variable shall be used to access your Django admin dashboard. For security purposes, it is a good idea to keep it as a short random string.
* `DJANGO_SECRET_KEY`  
A secret key used by Django for generating session cookies and other purposes. An online search will provide several methods for generating it.
* `FERNET_SECRET_KEY`  
__Required__  
A secret key used for encrypting patient records in the database. This can be generated in the same way as the Django secret key.
* `DJANGO_SETTINGS_MODULE`  
__Required__  
This variable specifies which settings to use in the production environment. Set the value to `config.settings.production` to point it to the production settings file in the project.
* `USE_S3`  
Set this variable to `True` if you want to use Amazon S3 buckets for storing your static files in production. Defaults to 'False'.
* `AWS_STORAGE_BUCKET_NAME`  
This variable is used to store the bucket name to store your static files during the collectstatic step. Note that this is used only if `USE_S3` is set to `True`.
* `AWS_ACCESS_KEY_ID`  
The AWS Access Key of your account used to access your S3 bucket. Note that this is used only when `USE_S3` is set to `True`.
* `AWS_SECRET_ACCESS_KEY`  
The AWS Secret Key of your account used to access your S3 bucket. Note that this is used only when `USE_S3` is set to `True`.
* `REDIS_URL`  
__Required__  
The URL to your Redis instance for use in caching.
* `SENTRY_DSN`  
__Required__  
The Sentry DSN value for logging errors from your app. To get a free DSN, sign up at <https://sentry.io>.
* `GOOGLE_RECAPTCHA_SITE_KEY`  
The configured site key for your recaptcha.
* `GOOGLE_RECAPTCHA_SECRET_KEY`  
The secret key for your recaptcha.
* `DJANGO_ALLOWED_HOSTS`  
This is used to store a JSON type array of hosts you want to allow access to your backend API. Requests with other Host fields will not be able to complete successfully. Set it to `['*']` to allow all hosts. Defaults to `['*']`.
* `CSRF_TRUSTED_ORIGINS`  
Contains a JSON array of hosts that are allowed to make cross site requests to the backend API. Defaults to `[]`.
* `DJANGO_SECURE_SSL_REDIRECT`  
Use this option to set whether or not you want to redirect from HTTP to HTTPS automatically. Defaults to `True`.
* `RATE_LIMIT`  
A string value of the form requests/time to be set for rate limiting. For eg., if you want to allow not more than 5 requests from a user in 10 mins, provide `5/10m` as the value. Defaults to `5/10m`.
* `MAINTENANCE_MODE`  
Set this variable to 1 to put the site/API into maintenance. Defaults to 0.
* `POSTGRES_DB`  
__Required__  
Your PostGIS DB name.
* `POSTGRES_HOST`  
__Required__  
Your Postgres host address.
* `POSTGRES_USER`  
__Required__  
Your Postgres username.
* `POSTGRES_PASSWORD`  
__Required__  
Your `POSTGRES_USER` password.
* `POSTGRES_PORT`  
__Required__  
Your Postgres instance port number.
