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
```

### Aliases

```bash
# Creates a new file in dbin to alias that command inside the docker container (use the --root flag if the command should be run as root)
$ dbin/mkalias [--root] <command>

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
$ source dbin/local-env
$ gem install rails
$ mkalias rails
$ mv README.md INSTRUCTIONS.md
$ rails new . --force
$ rails s
```