# REST League :: APIs

You can run your brand-new REST API testing tool on the two example APIs `languagetool` and `restcountries` provided in this folder.

Each API example contains
- A directory `classes` with the bytecode of the API
- A directory `specification` with the OpenAPI documentation 
- A Dockerfile building a Docker image of the API

You can setup an API by running the bytecode from the `classes` directory or by using the provide Docker image.

## API Setup

We recommend to use the Docker image. So, first you have to build the image
```
docker build -t <name-for-the-api-image> <api-dockerfile-directory>
```

Then, run the API within Docker
```
docker run <name-for-the-api-image>
```

## RESTgym

For a more extensive testing of your tool, you can use [RESTgym](https://github.com/SeUniVr/RESTgym), a benchmarking infrastructure specifically designed for REST API testing tools.