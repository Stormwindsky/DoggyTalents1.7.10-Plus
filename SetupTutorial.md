# Compiling DoggyTalents 1.7.10-Plus 🐾

This repository uses a modern RetroFuturaGradle (RFG) toolchain to compile Minecraft 1.7.10 mods using contemporary standards. Follow this guide to set up your environment and build the mod successfully on Linux (Ubuntu/Mint).

---

## Prerequisites

Before running any commands, ensure you have Java 17 installed. While the mod targets Minecraft 1.7.10 (Java 8), the modern Gradle wrapper requires Java 17 to execute the build system.

Install Java 17 and Git by running:

    sudo apt update && sudo apt install openjdk-17-jdk git -y

Verify your active Java version:

    java -version

(It should output openjdk version "17.x.x")

---

## Setup & Compilation Steps

### 1. Clone the Repository

    git clone https://github.com/Stormwindsky/DoggyTalents1.7.10-Plus.git
    cd DoggyTalents1.7.10-Plus

### 2. Fix the GTNH Remote Script Bug (Crucial)

The upstream GTNewHorizons build script contains a remote check that fails with a 404 Not Found error. You must disable this remote check before building.

Run this command to patch your local build.gradle automatically:

    sed -i 's|String availableBuildScript = availableBuildScriptUrl().newInputStream(parameters).getText()|String availableBuildScript = ""|g' build.gradle

### 3. Grant Execution Permissions

Give the Gradle wrapper executable permissions:

    chmod +x gradlew

### 4. Build the Mod

Run the compilation process. RetroFuturaGradle will automatically download Minecraft 1.7.10 assets, map dependencies, and inject your custom translations:

    ./gradlew build

---

## Output Location

Once the terminal displays BUILD SUCCESSFUL, your compiled .jar file will be generated inside the following directory:

    build/libs/

You can take the generated .jar file and drop it straight into your .minecraft/mods folder to test your new features and languages!

---

## Troubleshooting

- Java version error: If you have multiple Java versions installed, ensure Java 17 is active with sudo update-alternatives --config java.
- Permission denied: If ./gradlew fails to run, re-run chmod +x gradlew.
- Network issues: If asset download fails, check your internet connection or use a proxy.

---

Happy building! 🚀
