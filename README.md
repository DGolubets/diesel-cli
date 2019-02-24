# diesel-cli

[Diesel.rs](http://diesel.rs) command line tool Docker image.
It is based on Alpine to keep it as small as possible (~ 17 MB)

## Usage

### As CLI

Just use it as you would use diesel-cli:

```bash
docker run -it dgolubets/diesel-cli migration list
```

### As a base image for your migrations

Create a Dockerfile:

```Dockerfile
FROM dgolubets/diesel-cli:latest
COPY ./migrations ./migrations
CMD ["database", "setup"]
```

Build your migrations image:

```bash
docker build . -t migrations
```

Run migrations:

```bash
docker run -e DATABASE_URL=postgres://username:password@pghost/diesel_demo migrations:latest
```