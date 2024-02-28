# Testing Jenkins Sbom-Studio Plugin


## Contents
* Introduction
* Requirements
* Loading the Plugin
* Testing
* Test Cases
* Notes

## Introduction

This documentation concerns the testing of the Cybeats Jenkins Sbom-Studio Plugin including its installation and the execution of the Jenkinsfile test script.

## Requirements

* Local Jenkins installation.
* Cybeats Jenkins Sbom-Studio Plugin file (.hpi).
* Access to this repository.

## Loading the Plugin
To load the Jenkins plugin:

* Navigate to the Jenkins build URL for Cybeats, and download the release in question. Alternatively, the plugin can be obtained via local file.

* Unzip the downloaded file. You will then have a plugin file ".hpi" and an sbom.

* Go to your local Jenkins installation, and navigate to the "Manage Jenkins" button.

* Proceed to "Plugins".

* Proceed to "Advanced Settings".

* Scroll down to "Deploy Plugin", and load the plugin file.

* Restart Jenkins.

To check and verify correct installation, navigate to "Plugins" as before, and click on "Installed plugins". You should see "Cybeats Sbom Studio" as one of the installed plugins.

Authenticate your API by navigating to Manage Jenkins / System / Cybeats Sbom Studio. Insert your URL and insert your API keys as a secret text.

## Testing

To load the test:

* Create a new Pipeline in Jenkins.

* Select "GitHub project".

* Paste the repo url in the text box.

* In the Pipeline section, change the "Definition" to "Pipeline script from SCM".

* Change the SCM to "Git".

* Paste the repo url in the text box.

* Save.

To run the test:

* Navigate to the Pipeline.

* Click "Build With Parameters".

Note: The outcome of the build is a failure, this is expected.


## Test Cases

1. Check General Functionality - Expect success.
2. Check No Parameters - Expect fail - Please insert all required values.
3. Check Full Parameters - Expect success.
4. Check Invalid manufacturerId - Expect fail - ```Status code : 400
{"message":"Manufacturer Organization was not found"}```.
5. Check Invalid supplierId - Expect fail - ```Status code : 400
{"message":"Supplier Organization was not found"}```.
6. Check Wrong pkgType - Expect fail - Wrong configuration.
7. Blank pkgtype - Expect success.
8. Whitespace pkgtype - Expect fail - Wrong configuration.
9. Whitespace sbomComponentName - Expect success.
10. Whitespace sbomComponentNamespace - Expect success.
11. Whitespace sbomComponentVersion - Expect fail - Wrong configuration.
12. Blank subType - Expect fail - Please insert all required values.
13. Nonexistent file - Expect fail - File ```file-that-doesn't-exist``` was not found.
14. Check SBOM No Root Component - Expect fail - SBOM component is required, but was not provided by the user.
15. Check SBOM No Root Component With Metadata - Expect success.



## Notes

This Repo can be used locally, but it requires modification of the Jenkins service file. Add:

```Environment="JAVA_OPTS=-Dhudson.plugins.git.GitSCM.ALLOW_LOCAL_CHECKOUT=true"```










