# AdRevo Ph API

## Setup

```
git pull
bundle install
mv [your secret file] config/secret.yml
mv [your gss service account] config/gss_service_account.json
mysql -uroot www < db/views/*.sql
rake db:migrate
rake unicorn:start
```

## Update

```
# Apply app/controller change
ps aux | grep unicorn # check master process no
kill -9 [master process no]
rake unicorn:start

# Apply crontab change
vim config/schedule.rb
bundle exec whenever --update-crontab
bundle exec whenever --clear # if you want to stop
```

