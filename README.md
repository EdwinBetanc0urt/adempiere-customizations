# ADempiere Patches
Use this project to publish patches from ADempiere

## How to add a patch?
If you want to add a patch for a adempiere source folder just make the follow:
My example is adding the patch for `org.spin.loan_management`.

The file `settings.gradle` already have the loan management as folder
```
include (':' + rootProject.name + '.investment-and-loan')
project (':' + rootProject.name + '.investment-and-loan').projectDir = file('investment-and-loan')
```

- Add a subfolder named `investment-and-loan`
- Add it `api project(':adempiere-customizations.investment-and-loan')` inside main `build.gradle` below of `api project(':adempiere-customizations.base')`
- Inside folder add a gradle like the base gradle `base/build.gradle` (you can copy and paste it)
- Change the variable value `def packageName = "base"` by `def packageName = "investment-and-loan"` this is the final package name
- Add a folder `src/main/java`
- Add your patch with package inside folder


## Repository secrets

### General
- `DEPLOY_PUBLISH_GROUP`: Sets the group to publish, it is not mandatory, its default value is `io.github.adempiere`.

### To publish in GitHub packages

- `DEPLOY_PUBLISH_GITHUB_URL`: The path where packages will be published in github, its default value is `https://maven.pkg.github.com/adempiere/adempiere-customizations`, it must be changed unless you have write permission in that space. As a good practice use the name of the organization and the name of the repository containing the patches.
- `DEPLOY_REPOSITORY`: The path to the maven repository for downloading packages from github, it is not mandatory, default value is `https://maven.pkg.github.com/adempiere/adempiere`.
- `DEPLOY_USER`: The user name with write access to the package release repository.
- `DEPLOY_TOKEN`: The token generated for the previously indicated user, it should be noted that he/she must have access to read and write packages.

### To publish in Sonatype

- `DEPLOY_PUBLISH_SONATYPE_URL`: The path where packages will be published in sonatype, its default value is `https://s01.oss.sonatype.org/service/local/staging/deploy/maven2/`.
- `PGP_PASSPHRASE`: A GPG key is a pair of keys: a public key and a private key. The public key is distributed to verifiers, while the private key is kept secret and used to sign artifacts.
- `PGP_SECRET`: The private key is often protected by a passphrase. This passphrase is used to decrypt the private key and allows it to be used for signing.
- `OSSRH_USERNAME`: The user name with write access to the package release repository.
- `OSSRH_TOKEN`: The token generated for the previously indicated user.
