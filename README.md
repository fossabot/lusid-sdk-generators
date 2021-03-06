![LUSID_by_Finbourne](https://content.finbourne.com/LUSID_repo.png)
[![FOSSA Status](https://app.fossa.com/api/projects/git%2Bgithub.com%2Ffinbourne%2Flusid-sdk-generators.svg?type=shield)](https://app.fossa.com/projects/git%2Bgithub.com%2Ffinbourne%2Flusid-sdk-generators?ref=badge_shield)

This repository contains the generation and publishing logic for each of the LUSID SDKs currently there are SDKs for:
- Python
- Java
- Javascript (Typescript)
- CSharp

## Generate

If you would like to generate an SDK using a custom swagger.json file, please do the following:

1) Ensure that you have already checked out the project that you want to generate an SDK for e.g. https://github.com/finbourne/lusid-sdk-csharp
2) Navigate to the `/all/generate` directory in the lusid-sdk-generators (this) repo
3) Run the build.sh script passing in the following variables

    a) The name of the language that you would like to generate the SDK for e.g. `python`. Options are:
    
        - javascript
        - python
        - csharp
        - java
    
    b) The URL of the swagger.json file or the relative location of the file e.g. `https://fbn-prd.lusid.com/api/swagger/v0/swagger.json` or `../../../projects/lusid-ibor/lusid-0.10.8.3.json`
    
    c) The folder of your project you have already checked out e.g. https://github.com/finbourne/lusid-sdk-csharp into which the SDK should be generated, 
    this should be one level above the sdk folder e.g. `../../../projects/lusid-sdk-python`. 
    The generation only works if combined with the pre-existing SDKs specified as an output folder as there are some manually created files and tests in each SDK which
    won't be generated automatically
    
    A command might look something like this `sh build.sh csharp https://fbn-prd.lusid.com/api/swagger/v0/swagger.json ../../../work/projects/lusid-sdk-csharp`
    
    P.S. Please note you will need Docker installed and running to use the build.sh script
----
    
If you would like to modify the way that the SDK is generated you can edit the `generate.sh`, `config.json` or `.openapi-generator-ignore` files to suit your needs. Each of these files
is used by the `build.sh` script. 

These are also used in the pipeline so if you would like to update the way the SDK is generated in there you need to commit your changes and raise a merge request.

## Publish

If you would like to publish a generated SDK, please do the following:

1) Ensure that you have already checked out the project that you want to publish an SDK for e.g. https://github.com/finbourne/lusid-sdk-csharp
2) If publishing a new SDK, ensure that you have already generated the SDK following the instructions above and set the version to have your initials at the end e.g. `0.10.705-MM`. You will
want to ensure the version is set in the appropriate file e.g. package.json, __version__.py etc. and in the swagger file you used to generate the SDK
2) Navigate to the `/all/publish` directory in the lusid-sdk-generators (this) repo
3) Run the publish.sh script passing in the following variables

    a) The name of the language that you would like to generate the SDK for e.g. `python`. Options are:
    
        - javascript
        - python
        - csharp
        - java
    
    b) The folder of your project from which the SDK should be published, this should be one level above the sdk folder e.g. `../../../projects/lusid-sdk-python`
    
    c) The API key or password for publishing to a remote repository
    
    d) The URL or name of the remote repository to publish to e.g. `https://hosted_package_manager_url`.
    
    A command might look something like this `sh publish.sh python ../../../lusid-sdk-python abc_secret_api_key https://hosted_package_manager_url`
   
    P.S. Please note you will need Docker installed and running to use the publish.sh script
----
    
If you would like to modify the way that the SDK is published you can edit the `publish.sh` files to suit your needs.

These are also used in the pipeline so if you would like to update the way the SDK is published in there you need to commit your changes and raise a merge request.


## License
[![FOSSA Status](https://app.fossa.com/api/projects/git%2Bgithub.com%2Ffinbourne%2Flusid-sdk-generators.svg?type=large)](https://app.fossa.com/projects/git%2Bgithub.com%2Ffinbourne%2Flusid-sdk-generators?ref=badge_large)