# Omegapoint CI/CD Training - Sample One

This project is used for training.

# Build and run

## Native

To make a new build:

```bash
$ ./gradlew clean build
```

To run locally:

```bash
$ ./gradlew bootRun
```

The application will be available on `http://localhost:8080`

## Container

The project uses [Google Jib][1] to build Docker images with the application. In CI/CD the image will be pushed to an image registry by running:

```bash
$ ./gradlew jib
```

The image can also be built with a local Docker daemon for testing with:

```bash
$ ./gradlew jobDockerBuild
```

[1]: https://github.com/GoogleContainerTools/jib
