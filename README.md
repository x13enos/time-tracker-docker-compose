# time-tracker-docker-compose

Basically it's just a docker compose that launches several containers for backend, frontend, nginx, postgres, certbot and crontasks.

For launching this on another instance you should: 
- Clone this app to your instance
- Changed the domains in `init-letsencrypt.sh` and `./data/nginx/app.conf`
- Updated env variables in `.env` and `.front-env`
- Create the certificates with the `./init-letsencrypt.sh`
- Launch `docker-compose up -d`
- For backups please add `0 0 * * * docker run --env-file ./.env --network=#{network} x3enos/ruby_backup:temp1` to crontab 

Do not forget to create and populate(optionaly in case you have the dump) DB.

During the setting up i've used the following articles:
https://scotto.medium.com/2021-docker-ruby-3-rails-6-puma-nginx-postgres-d84c95f68637
https://pentacent.medium.com/nginx-and-lets-encrypt-with-docker-in-less-than-5-minutes-b4b8a60d3a71
