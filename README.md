# Let's go to the Ruby on Rails 
A little app for discovery the magnifient Ruby.  

## Installation
_The installation it's easy with Docker. You should just follow instructions below:_
```bash
$ docker-compose run app rails new . --force --database=mysql --skip-bundle
```

> __Great !__  
> Your application is already ready !

Because you have a new Gemfile, you should rebuild your application for copy in your container.
```bash
$ docker-compose build
```

## Database

### Configuration
_Now, change your database configuration in `config/database.yml`_
```yml
default: &default
  adapter: mysql2
  encoding: utf8
  pool: 5
  username: root
  password: "root"
  host: db

development:
  <<: *default
  database: dev

test:
  <<: *default
  database: dev
```

### Creation
_It's easy launch these commands_
```bash
# Launch the container in the detach mode
$ docker-compose up -d

# Create your database
$ docker-compose run app rake db:create
```

### Tips
Sometimes, when you modify your files, nothing is happening...  
So, you have to change in your configuration `config/environments/development.rb`
```ruby
config.file_watcher = ActiveSupport::EventedFileUpdateChecker
```
change `EventedFileUpdateChecker` by `FileUpdateChecker`
> **Magic !**
```ruby
config.file_watcher = ActiveSupport::FileUpdateChecker
```
## The result 
_You can play with your application, before, you can show your ip machine of your VM with this command_
```bash
$ docker-machine ip default
192.168.99.100
```

> **Lift-off**  
> 192.168.99.100:3000









