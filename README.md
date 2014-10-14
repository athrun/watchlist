# Movie Watchlist

This is a sample rails app to illustrate migrating from Heroku to AWS Beanstalk.

This app rely on the following components to work:

- PostgreSQL database
- Redis instance (for [Sidekiq](http://sidekiq.org/))
- SMTP gateway like Amazon SES or Mandrill (for sending `devise` forgot password emails)

The environment variable needed are:

- RACK_ENV (production)
- RAILS_ENV (production)
- HOST (e.g. wagon-watchlist.herokuapp.com)
- MANDRILL_USERNAME
- MANDRILL_APIKEY
- DEVISE_SECRET_KEY (e.g. `ruby -rsecurerandom -e "puts SecureRandom.hex(64)"`)
- SECRET_KEY_BASE (idem)
- S3_BUCKET_NAME
- AWS_ACCESS_KEY_ID
- AWS_SECRET_KEY
- `REDIS_PROVIDER` or `REDIS_URL`
- RDS_HOSTNAME
- RDS_PORT
- RDS_DB_NAME
- RDS_USERNAME
- RDS_PASSWORD

This app uses S3 and ImageMagick (Paperclip). The `Procfile` has 2 lines,
a `web` and a `worker`.

## Running this app on AWS

### Steps

1. Create an AWS account: https://portal.aws.amazon.com/gp/aws/developer/registration/index.html?nc2=h_ct
2. Create a S3 Bucket
3. Launch a PostgreSQL instance using Amazon RDS: http://docs.aws.amazon.com/AmazonRDS/latest/UserGuide/CHAP_GettingStarted.CreatingConnecting.PostgreSQL.html
4. Launch a Redis node for Sidekiq using Amazon ElastiCache: http://docs.aws.amazon.com/AmazonElastiCache/latest/UserGuide/GettingStarted.html
5. Deploy the app in Elastic Beanstalk: http://docs.aws.amazon.com/elasticbeanstalk/latest/dg/create_deploy_Ruby_rails.html
6. Adjust the environment variables accordingly


