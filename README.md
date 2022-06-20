# ruby-base

## Usage

### Base commands

```bash
# Runs the command inside an ephemeral container using the app service described in the docker-compose file as a base (use the --root flag if the command should be run as root)
$ dbin/run [--root] <command>

# Rebuild the image after any changes to the dockerfile
$ dbin/build

# Remove all containers and their volumes (WARNING any cache or files not stored in the filesystem will be deleted)
$ dbin/dispose

# Moves the target folder contents to the root folder and deletes the target folder
# it also renames this file to INSTRUCTIONS.md
$ dbin/mvroot <target>

# Appends a RUN command to the base image, useful to install new packages
$ dbin/chimg <command>
```

### Aliases

```bash
# Creates a new <name> file in dbin to alias the <command> inside the docker container (use the --root flag if the command should be run as root)
$ dbin/mkalias [--root] <name> <command>

# Opens a new terminal in the project folder (use the --root flag if the shell should assume the root user)
$ dbin/shell [--root]

# Runs gem in the project folder
$ dbin/gem

# Runs bundle in the project folder
$ dbin/bundle
```

### Helpers

```bash
# Adds dbin folder to the PATH only for the current terminal session.
$ source dbin/local-env

# After using this command you can use the any script inside the dbin folder without the dbin/ prefix
```

## Examples

### Rails app
```bash
# (optional) Add the dbin/ folder to your PATH, if you choose to do this step, all commands will be available without the dbin/ prefix
$ source dbin/local-env

# Install rails
$ dbin/gem install rails

# Installing the database libs

# if using PostgreSQL:
$ dbin/chimg sudo apk add postgresql-client postgresql-dev

# if using MySQL:
$ dbin/chimg sudo apk add mysql-client mysql-dev

# if using SQLite:
$ dbin/chimg sudo apk add sqlite sqlite-dev


# Rename this file so rails doesn´t overwrites it
$ mv README.md USAGE.md

# Create a new rails app
$ dbin/run rails new . --force [--database [sqlite3 | postgresql | mysql]]

# Create an alias for using the local app rails
$ dbin/mkalias bin/rails

# Start the application
$ dbin/rails s
```