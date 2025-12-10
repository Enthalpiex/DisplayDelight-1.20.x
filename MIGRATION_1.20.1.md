# Migration to Minecraft 1.20.1

This document describes the changes made to migrate Display Delight from Minecraft 1.21.1 to 1.20.1.

## Changes Made

### 1. gradle.properties
- `minecraft_version`: 1.21.1 → 1.20.1
- `loader_version`: 0.18.1 → 0.14.24
- `loom_version`: 1.13-SNAPSHOT → 1.3.8
- `mod_version`: 1.5.0-mc1.21.1 → 1.5.0-mc1.20.1
- `fabric_version`: 0.116.7+1.21.1 → 0.92.2+1.20.1

### 2. build.gradle
- Java version: 21 → 17
  - Changed `it.options.release = 21` to `it.options.release = 17`
  - Changed `JavaVersion.VERSION_21` to `JavaVersion.VERSION_17`
- Loom version: Updated to 1.3.8 (stable release for 1.20.1)

### 3. src/main/resources/fabric.mod.json
- `fabricloader`: ">=0.16.14" → ">=0.15.0"
- `minecraft`: "~1.21.1" → "~1.20.1"
- `java`: ">=21" → ">=17"

## Building the Project

### Requirements
- Java 17 or later
- Access to maven.fabricmc.net (required for Fabric Loom)
- Gradle 8.1+ (uses wrapper, so no manual installation needed)

### Build Commands

```bash
# Clean and build
./gradlew clean build

# Just build
./gradlew build

# Run client
./gradlew runClient

# Run server
./gradlew runServer
```

## Potential Code Changes

After the build succeeds, you may need to address API changes between 1.21.1 and 1.20.1:

1. **Check for removed/renamed methods**: Minecraft 1.21.x introduced some API changes
2. **Review deprecated APIs**: Some methods may have been deprecated in 1.20.1
3. **Test thoroughly**: Run the mod in-game to ensure all features work correctly

## Compatibility Notes

- Fabric Loader 0.14.24 is compatible with Minecraft 1.20.1
- Fabric API 0.92.2+1.20.1 is the recommended version for this Minecraft version
- Loom 1.3.8 provides full support for Minecraft 1.20.1 development

## Network Requirements

**Important**: Building this project requires access to https://maven.fabricmc.net/
If you're in a restricted network environment, you may need to:
- Use a VPN or proxy
- Set up a local Maven mirror
- Contact your network administrator

## Troubleshooting

### Build fails with "Could not resolve net.fabricmc:fabric-loom"
- Check your internet connection
- Verify you can access https://maven.fabricmc.net/
- Try running with `--refresh-dependencies` flag

### Compilation errors after successful build setup
- Review the specific error messages
- Check if any APIs were removed or changed between 1.21.1 and 1.20.1
- Consult the Minecraft/Fabric API changelogs

## Next Steps

1. Build the project locally where maven.fabricmc.net is accessible
2. Run automated tests if available
3. Manual testing in Minecraft 1.20.1
4. Fix any compilation errors or runtime issues
5. Update documentation and changelog
