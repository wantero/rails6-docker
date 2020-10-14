# Template for Rails6 App with PostgreSQL using Docker

Template project using Rails 6 with PostgreSQL + Docker

## Build the project

With those files in place, you can now generate the Rails skeleton app using docker-compose run:

```
docker-compose run --no-deps web rails new . --force --database=postgresql
```

Now that you’ve got a new Gemfile, you need to build the image again. (This, and changes to the Gemfile or the Dockerfile, should be the only times you’ll need to rebuild.)

```
docker-compose build
```

## Connect the database

Replace the contents of config/database.yml with the following:

```
default: &default
  adapter: postgresql
  encoding: unicode
  host: db
  username: postgres
  password: password
  pool: 5

development:
  <<: *default
  database: myapp_development


test:
  <<: *default
  database: myapp_test
```

You can now boot the app with docker-compose up:

```
docker-compose up
```

Finally, you need to create the database. In another terminal, run:

```
docker-compose run web rake db:create
```

## View the Rails welcome page!

http://localhost:3000

## More info:
https://docs.docker.com/compose/rails/