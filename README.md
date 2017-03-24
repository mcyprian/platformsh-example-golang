# Go template for Platform.sh

This project provides a starter kit for Go projects hosted on Platform.sh. It is primarily an example, although could be used as the starting point for a real project.

## Starting a new project

To start a new project based on this template, follow these 3 simple steps:

1. Clone this repository locally.  You may optionally remove the `origin` remote or remove the `.git` directory and re-init the project if you want a clean history.
 
2. Create a new project through the Platform.sh user interface and select "Import an existing project" when prompted.

3. Run the provided Git commands to add a Platform.sh remote and push the code to the Platform.sh repository.

That's it!  You now have a working "hello world" level project you can build on.

## Structure

Go requires a GOPATH to be set, and for an application to be nested within it.  However, the Platform.sh build environment does not directly have such a structure.  Instead, this repository uses a modified version of the [CloudFlare Hellogopher](https://github.com/cloudflare/hellogopher) Makefile.  This Makefile allows you simply push this repository to Platform.sh and allow it to build, either with a pre-committed vendor directory or downloading dependencies on the fly.

To setup your local checkout, run:

```bash
make setup
make deps
```

The first command should be run only once to initialize the project.  The second will download dependencies to the `vendor` directory using `gvt`.  To change the dependencies to download modify the `deps` target at the top of the `Makefile`.  You are of course free to use any other vendoring tool you wish.

To compile the application, run `make` with no arguments.  That will compile your application and place the resulting binary in the `bin` directory.

See the documentation at the top of the `Makefile` for more information.  If you choose to commit your `vendor` directory to your repository, you can remove the `make deps` step from the build hook in `.platform.app.yaml`.
