# Meteor Client 0.5.4 — Connector compatibility build

This is a community-maintained source fork of [Meteor Client](https://github.com/MeteorDevelopment/meteor-client), prepared for one reported setup: **Minecraft 1.20.1, Forge 47.4.10, and Sinytra Connector**.

The original project is a Fabric mod. This repository does not turn Meteor into a native Forge mod; Connector provides the Fabric compatibility layer. The maintainer reports that this build starts in the setup above after Meteor's Baritone integration was removed. Results can vary with other mod lists and Connector versions.

## What changed

- Removed Meteor's Baritone API integration from the affected source files. Baritone-dependent features are unavailable in this build.
- Kept the rest of the Meteor Client 0.5.4 source tree and its upstream license notices.
- The complete cleaned source tree is available in [`meteor-client-forge-connector-compat-source.zip`](meteor-client-forge-connector-compat-source.zip). The standalone [`baritone-removal.patch`](baritone-removal.patch) and [`PATCH-GUIDE.md`](PATCH-GUIDE.md) are also in this repository. Inside the source archive, the patch is under `patches/baritone-removal.patch`.

## Build

Use Java 17. From the repository root on Windows, run:

```powershell
.\gradlew.bat build
```

On macOS or Linux, run `./gradlew build`. The packaged jar is created under `build/libs/`; the working project produced `meteor-client-0.5.4-all.jar`.

## Install

1. Use a Minecraft 1.20.1 instance with Forge 47.4.10 and a compatible Sinytra Connector installation.
2. Copy the built `meteor-client-0.5.4-all.jar` into that instance's `mods` folder.
3. Remove other Meteor Client jars from the same instance to avoid loading two versions.
4. Launch the instance. Addons and other mods may need separate compatibility work.

Connector and Forge releases can change compatibility. This build does not guarantee compatibility with every modpack, addon, or loader combination.

## Verify a jar with SHA-256

After building or downloading a jar, calculate its SHA-256 and compare the result with the checksum published for that exact file:

```powershell
Get-FileHash .\build\libs\meteor-client-0.5.4-all.jar -Algorithm SHA256
```

On macOS or Linux:

```sh
sha256sum build/libs/meteor-client-0.5.4-all.jar
```

Checksums are specific to a particular jar. Rebuilding from source can produce a different hash, so do not compare a locally rebuilt jar with a checksum for a separately built release artifact.

## Known limitations

- The codebase is still a Fabric mod and depends on Connector for the Forge setup described above.
- Baritone integration and its dependent features are removed.
- Compatibility is only reported for Minecraft 1.20.1 + Forge 47.4.10 + Sinytra Connector; other combinations are not established here.
- This is a community fork, not an official Meteor Development release. Please report problems with the exact Forge, Connector, Java, and mod versions.

## Credits and license

Meteor Client was created by [Meteor Development](https://github.com/MeteorDevelopment/meteor-client). This fork retains the upstream source and notices and is distributed under the same **GNU General Public License v3.0 (GPL-3.0)**. See [`LICENSE`](LICENSE) for the full license. Modified source is identified here and in the patch; upstream authors are not responsible for this fork.

Upstream project: <https://github.com/MeteorDevelopment/meteor-client>
