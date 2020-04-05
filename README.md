# Udagram Image Filtering Microservice

A simple image processing microservice, as part of the Udacity Cloud Developer Nanodegree (Project 2). It is a Node-Express application that resizes the image and runs it through a greyscale filter. The application is intended to be deployed on AWS Elastic Beanstalk.

## Prerequisites

### Node.js and NPM

Before getting started, make sure Node.js is downloaded and installed. The latest version of Node.js can be downloaded from [nodejs.org](https://nodejs.com/en/download) and it's recommended to use the LTS version.

### AWS CLI

It is recommended to use the AWS CLI for managing and configuring AWS. Installation instructions can be found [here](https://docs.aws.amazon.com/cli/latest/userguide/install-cliv2.html) and details on configuring AWS credentials can be found [here](https://docs.aws.amazon.com/cli/latest/userguide/cli-chap-configure.html).

### EB CLI

Elastic Beanstalk CLI is used for creating and deploying to your Elastic Beanstalk environment. Installation instructions can be found [here](https://docs.aws.amazon.com/elasticbeanstalk/latest/dg/eb-cli3-install.html).

## Getting Started

### Development Server

The application runs as a node server. Open a new terminal within the project directory and run:

1. Install dependencies: `npm i`
2. Run the development server: `npm run dev`

_Note: Default URL for the development server will be `http://localhost:{{PORT}}/`._

### Elastic Beanstalk Deployment

1. Initialize an EB CLI project
2. Create deployable build
3. Create new environment
4. Deploy changes

_Note: URL for the Elastic Beanstalk server can be found on the EB application dashboard (See deployment screenshot)._

#### Initialize Your EB CLI Project

Run `eb init`, in the project folder, to initialize an EB CLI project for the first time.

Once completed, open `.easticbeanstalk/config.yml`, from within the project folder, and add the following:
```
deploy:
    artifact: ./www/Archive.zip
```

#### Create Deployable Build

To create a deployable build and produce an Archive.zip file in the build directory, run `npm run build`.
_Note: If build command produces an error (in windows) try git running the command in git bash._

#### Create New Environment

Run `eb create` to create a new EB environment and push the initial build of the application.

_Note: A deploayble build must be created before creating a new EB environment_

#### Deploy Application

Changes to the application can be deployed using `eb deploy`.

## API Endpoints

**`GET /`**

Simply returns a message with usage instructions.

**`GET /filteredimage?image_url={{}}`**

Requires the url of an image. The image will be resized, run through a greyscale filter and the new image returned as a JPEG.

Example:
```
http://localhost:{{PORT}}/filteredimage?image_url=filteredimage?image_url=https://cdn.fileinfo.com/img/ss/lg/jpeg_43.jpg
```

## Acknowledgements

This project was bootstrapped with the Udacity [Image Filter Starter Code](https://github.com/udacity/cloud-developer/tree/master/course-02/project/image-filter-starter-code).
