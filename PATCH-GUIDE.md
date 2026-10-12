# Applying the Baritone-removal patch

The patch records the working-tree changes captured from the project's saved pre-removal copies. It changes 13 Java files. It was created for the Meteor Client 0.5.4 source tree in this project and may not apply cleanly to another revision.

1. Obtain the matching Meteor Client 0.5.4 source and keep a clean backup.
2. From the source root, apply the patch:

   ```sh
   git apply --check patches/baritone-removal.patch
   git apply patches/baritone-removal.patch
   ```

3. Build with Java 17 using `./gradlew build` (or `gradlew.bat build` on Windows).
4. Review the resulting changes and test them in your own Minecraft 1.20.1 + Forge 47.4.10 + Connector instance.

If `git apply --check` reports conflicts, stop and compare the affected files manually. Do not force the patch onto a different Meteor version. Keep the upstream `LICENSE` and source copyright notices when redistributing modified source or binaries, and make the modified source available under GPL-3.0 as required by the upstream license.
