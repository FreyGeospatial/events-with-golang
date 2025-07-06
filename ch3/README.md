# Quick Start:

To spin up the kafka environment, run `docker compose up` in the directory containing the docker compose file.

Use `docker ps` to check that the images are running.

Assuming you have `go` already installed, `cd` to the `/publisher` directory, and run `go mod init publisher`, followed by `go mod tidy`. The `mod init` command will initialize the directory as a module, and `mod tidy` will attempt to install any 3rd party dependencies.

Then, do the same while in the `/subcriber` directory.

Run the publisher using `go run publisher.go`.