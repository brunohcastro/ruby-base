# ruby-base

## Usage

If you want to start a rails application, you can clone this repo to the project folder and run the following commands:

```bash
$ ./docker/run gem install rails
$ ./docker/run rails new . --force --database=sqlite3
```

If you want to use another database, you'll need to edit the `./docker/Dockerfile` and uncomment the desired database dependencies.

To rebuild the image after any changes to the dockerfile, run:

```bash
$ ./docker/build
```

To of dispose all container and volumes, run:

```bash
$ ./docker/dispose
```