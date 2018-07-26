
* [Build and Deploy without CI](#building-and-deploying-without-ci)
    * [quickbuild.sh](#quickbuild)
    * [quickdeploy.sh](#quickdeploy)


## Building and Deploying without CI
  Building an artifact and deploying it without going through the entire CI pipeline is accomplished via 2 scripts.  1 that builds the artifact in a local docker container and another that uploads the artifact to the "deploy" s3 bucket, then calls a script on the instance using Amazon SSM

  #### quickbuild
    quickbuild.sh requires a single argument, which is the name of the environment that will be passed to the actual build commands.  This must be one of "int", "stg", "uat", or "prod".  quickbuild.sh should be run from the directory where the script resides, i.e. from the root of the repository.  If the build process is successful, the resulting artifact will be copied back to the root of the repository.

  #### quickdeploy
    quickdeploy.sh requires at least 1 argument and at most 2.  The first argument must be the name of the environment where the artifact will be deployed.  The 2nd argument should be the path to a local file that will be deployed to the specified environment.  If this second argument is omitted, quickdeploy will simply deploy the artifact that is already in the "deploy" s3 bucket.
