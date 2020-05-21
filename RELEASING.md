Releasing
========

In order to deploy artifacts to a Maven repository, you'll need to set two properties in your private
Gradle properties file (`~/.gradle/gradle.properties`):

```
SONATYPE_NEXUS_USERNAME=<username>
SONATYPE_NEXUS_PASSWORD=<password>
```

 1. Change the version in `gradle.properties` to a non-SNAPSHOT version.
 2. Update the `CHANGELOG.md` for the impending release.
 3. Update the gradle coordinates in the README.
 4. `git commit -am "Prepare for release X.Y.Z."` (where X.Y.Z is the new version)
 5. `./gradlew clean uploadArchives`.
 6. Visit [Sonatype Nexus](https://oss.sonatype.org/) and promote the artifact.
 7. `git tag -a X.Y.X -m "Version X.Y.Z"` (where X.Y.Z is the new version)
 8. Update the `gradle.properties` to the next SNAPSHOT version.
 8. `git commit -am "Prepare next development version."`
 10. `git push && git push --tags`

If step 5 or 6 fails, drop the Sonatype repo, fix the problem, commit, and start again at step 4.
