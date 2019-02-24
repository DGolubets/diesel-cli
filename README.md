# diesel-cli

Diesel.rs command line tool Docker image.
It is based on Alpine to keep it as small as possible (~ 17 MB)

## Usage

### As CLI

Just use it as you would use diesel-cli:
```docker run -it dgolubets/diesel-cli migration list```

### As a base image for your migrations

Create a Dockerfile:

```Dockerfile
FROM dgolubets/diesel-cli:latest
COPY ./migrations ./migrations
CMD ["migration", "list"]
```

Build your migrations image:
```docker build . -t migrations```

Run migrations:
``` docker run -e DATABASE_URL=postgres://postgres:postgres@localhost:5432/mydb migrations:latest```