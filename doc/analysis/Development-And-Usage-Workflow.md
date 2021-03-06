# Development and usage workflow

Below a description of the planned development and usage process. Comments and progress are reported on [issue #42](https://github.com/open-license-manager/licensecc/issues/42)

![dev-build-process](https://user-images.githubusercontent.com/1121667/64474031-e5afff80-d1a0-11e9-9819-f3b7e4e2126d.png)

## Build release
Open License Manager developers build a new release merging code to the master branch. Implementing [GitFlow](https://nvie.com/posts/a-successful-git-branching-model) this should happen only when a new release is ready to be deployed.
Travis CI builds the release for the supported environments and deploys it to GitHub release system.

### Binary release contents
Binary release contains: 
 * license generator executable (`lccgen`).
 * source code of the unconfigured library.
 * source code of (part of) the tests.
 
### Test (1)
Contextually to the previous step Travis CI carries out all the tests.
A special attention is about how carry out functional tests. 
In this phase the library is configured, compiled (only for the tests sake), linked with a mock executable and tested together with the license generator.

## Initialize library
In this phase the signing keys are generated by license generator executable (`lccgen`), and optionally the source code of the library may be modified or obfuscated.

### Test (2)

## Integrate into the product
The source code of the library can and should be manually altered to prevent hackers to find a single cracking mechanism for all the products that integrate the library.

## deliver the product to the client
Compiled product is delivered to the client. 
 * If we want to link the execution to a specific hardware we need to send the product to the client without a license (or a demo executable, with the sole intent to generate the machine identifier). 
 * If we just want to send a demo product with an expiry date we prepare a license without the machine identifier.
 
## Build process
From the process described above, (strange to say) the license generator (`lcc`) configures itself as a build 
dependency of the licensing library, thus it needs to be built first.