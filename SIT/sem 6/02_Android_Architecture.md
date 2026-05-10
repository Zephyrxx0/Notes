# Topic 2 — Android Architecture, SDK, IDE & Build Process

> **Syllabus hours:** 6 &nbsp;|&nbsp; **Exam weight:** High

---

## 2.1 Android System Architecture

Android is designed as a layered stack. Each layer provides services to the layer above it. Think of it like a building — the foundations (Linux Kernel) support everything on top.

```
 ╔══════════════════════════════════════════════════╗
 ║  LAYER 5 — APPLICATIONS                          ║
 ║  Contacts · Phone · Browser · YOUR APP           ║
 ╠══════════════════════════════════════════════════╣
 ║  LAYER 4 — APPLICATION FRAMEWORK (Java APIs)     ║
 ║  Activity Manager  · View System                 ║
 ║  Content Providers · Location Manager            ║
 ║  Notification Manager · Resource Manager         ║
 ╠══════════════════════════════════════════════════╣
 ║  LAYER 3 — ANDROID RUNTIME (ART)                 ║
 ║  Core Java Libraries                             ║
 ║  ART (Android Runtime) / Dalvik VM               ║
 ╠══════════════════════════════════════════════════╣
 ║  LAYER 2 — C / C++ LIBRARIES                     ║
 ║  SQLite · WebKit · OpenGL/ES · libc · Media Fw   ║
 ╠══════════════════════════════════════════════════╣
 ║  LAYER 1 — LINUX KERNEL                          ║
 ║  Display · Camera · WiFi · Bluetooth drivers     ║
 ║  Power Management · Memory Management · Security ║
 ╚══════════════════════════════════════════════════╝
```

---

### Layer 1: Linux Kernel

The very bottom of the stack. The Linux Kernel handles:
- **Hardware Abstraction** — talks directly to the CPU, RAM, display hardware
- **Device Drivers** — software that controls physical hardware (WiFi, camera, touchscreen, audio)
- **Security** — each app runs in its own isolated user account (sandbox)
- **Power Management** — wakelocks, battery optimization
- **Memory Management** — allocating and freeing RAM

> **Why Linux?** Linux is proven, open-source, and has a huge driver ecosystem. Google modified it for mobile (lower power, no swap space, etc.)

---

### Layer 2: Native C/C++ Libraries

Libraries written in C or C++ that power the core features of the OS:

| Library | Purpose |
|---------|---------|
| **libc** | The standard C library — foundation for all programs |
| **SQLite** | A lightweight, relational database built into every Android device |
| **WebKit** | The browser rendering engine (powers the WebView widget) |
| **OpenGL ES** | 3D graphics rendering (games, maps) |
| **Media Framework** | Playing and recording audio/video (MP3, H.264…) |
| **SSL** | Secure network communications (HTTPS) |

---

### Layer 3: Android Runtime (ART)

This is where Android apps actually **execute**.

#### The JVM vs ART — why they are different

Normal Java runs on a **JVM (Java Virtual Machine)**. Android does NOT use a standard JVM. Instead, it uses **ART (Android Runtime)**, which was designed for mobile constraints:

| Feature | Standard JVM | Android ART |
|---------|-------------|-------------|
| Format | Runs `.class` bytecode | Runs `.dex` (Dalvik Executable) files |
| Compilation | JIT (Just In Time) | AOT (Ahead of Time) since Android 5 |
| Memory | High | Optimized for low RAM |
| Speed | Good | Optimized for battery and mobile CPU |

> **Older devices** used **Dalvik** (Android's previous runtime). ART replaced Dalvik in Android 5.0 (Lollipop). Dalvik used JIT (compiling at run time); ART uses AOT (compiling at install time), making apps start and run faster.

#### Core Java Libraries
Android also includes a subset of the Java Standard Library classes (`java.lang`, `java.util`, `java.io`, etc.) so you can use familiar Java features like `String`, `ArrayList`, and `HashMap`.

---

### Layer 4: Application Framework

This is the layer **you use as a developer**. It provides the high-level Java APIs you call in your code. Key managers:

| Manager | What it does |
|---------|-------------|
| **Activity Manager** | Manages the lifecycle of activities (when they start, pause, stop, die) |
| **View System** | Provides all UI building blocks (buttons, text views, layouts) |
| **Content Providers** | Standard interface for sharing data between apps |
| **Resource Manager** | Accesses non-code resources (strings, images, layouts) |
| **Location Manager** | Provides GPS and network-based location |
| **Notification Manager** | Shows notifications in the status bar |
| **Telephony Manager** | Access to phone calls and SMS |
| **Package Manager** | Information about installed apps |

---

### Layer 5: Applications

The topmost layer. This includes:
- **Built-in apps:** Contacts, Phone, Browser, Settings, Messages, Camera
- **Your apps:** Everything you build and install

All apps — including built-in ones — have equal access to the APIs. There is no "super" app.

---

## 2.2 Android SDK (Software Development Kit)

The **Android SDK** is the complete toolkit you download to develop Android apps. It includes:

| Component | Purpose |
|-----------|---------|
| **Android APIs** | The Java classes you call (`Activity`, `View`, `Intent`…) |
| **Build Tools** | `aapt`, `dx`/`d8`, `apksigner` — tools that compile and package your app |
| **Android Emulator** | A virtual Android device running on your PC |
| **ADB** (Android Debug Bridge) | Command-line tool to communicate with a real or virtual device |
| **SDK Manager** | Downloads different API levels and tools |
| **AVD Manager** | Creates and manages virtual devices |
| **Platform Tools** | Low-level tools like `adb` and `fastboot` |

### SDK Manager
The SDK Manager (inside Android Studio: **Tools → SDK Manager**) lets you download:
- Different Android platform versions
- Android build tools
- Google Play Services
- Emulator system images

---

## 2.3 Android Studio IDE

**Android Studio** is the official IDE (Integrated Development Environment) for Android development. It is built on **IntelliJ IDEA** by JetBrains.

### Why Android Studio?
- Code completion and error highlighting
- Visual layout editor (drag-and-drop UI design)
- Integrated emulator management
- Built-in Gradle build system
- Profiler tools for performance analysis
- Git version control integration

### Project Structure (Key Folders)
```
MyApp/
 ├── app/
 │    ├── src/
 │    │    └── main/
 │    │         ├── java/
 │    │         │    └── com.example.myapp/
 │    │         │         └── MainActivity.java   ← Your Java code
 │    │         ├── res/
 │    │         │    ├── layout/
 │    │         │    │    └── activity_main.xml   ← Your UI layouts
 │    │         │    ├── values/
 │    │         │    │    ├── strings.xml          ← Text strings
 │    │         │    │    └── colors.xml           ← Colour definitions
 │    │         │    └── drawable/                 ← Images, icons
 │    │         └── AndroidManifest.xml            ← App configuration
 │    └── build.gradle                             ← App-level build config
 └── build.gradle                                  ← Project-level build config
```

### AndroidManifest.xml — The App's ID Card
Every Android app must have this file. It declares:
- The app's package name (unique identifier)
- All activities, services, and broadcast receivers
- Permissions the app needs (internet, camera, etc.)
- The minimum and target SDK versions
- The launcher (main) activity

```xml
<?xml version="1.0" encoding="utf-8"?>
<manifest xmlns:android="http://schemas.android.com/apk/res/android"
    package="com.example.myapp">

    <!-- Permissions -->
    <uses-permission android:name="android.permission.INTERNET" />

    <application
        android:label="My App"
        android:icon="@mipmap/ic_launcher">

        <!-- Declare the main (launcher) activity -->
        <activity android:name=".MainActivity">
            <intent-filter>
                <!-- These two lines make this the LAUNCH activity -->
                <action android:name="android.intent.action.MAIN" />
                <category android:name="android.intent.category.LAUNCHER" />
            </intent-filter>
        </activity>

    </application>
</manifest>
```

---

## 2.4 The Android Build Process

This is a frequently examined topic. Understanding how `.java` source code becomes an `.apk` file is essential.

### Step-by-Step Build Diagram
```
Your Source Files
 ┌───────────────────┐
 │  .java files      │  ← Your Activity, helper classes
 │  .kt files        │  ← (Kotlin, if used)
 └─────────┬─────────┘
           │  Step 1: Java Compiler (javac)
           ▼
 ┌───────────────────┐
 │  .class files     │  ← Standard Java bytecode
 └─────────┬─────────┘
           │  Step 2: dx / d8 tool
           │  (Converts standard bytecode to Dalvik bytecode)
           ▼
 ┌───────────────────┐
 │  classes.dex      │  ← Dalvik Executable — runs on ART
 └─────────┬─────────┘
           │
           │          ┌──────────────────────────┐
           │          │  Resources                │
           │          │  (XML layouts, images,    │
           │          │   strings, icons)         │
           │          └────────────┬─────────────┘
           │                       │  Step 3: aapt tool
           │                       │  (Android Asset Packaging Tool)
           │                       │  Compiles XML, generates R.java
           └───────────────────────┤
                                   ▼
                        ┌─────────────────┐
                        │   .apk file     │  ← Android Package (unsigned)
                        └────────┬────────┘
                                 │  Step 4: apksigner / jarsigner
                                 ▼
                        ┌─────────────────┐
                        │  Signed .apk    │  ← Ready to install!
                        └─────────────────┘
```

### Key Tools Explained

| Tool | Full Name | What it Does |
|------|-----------|-------------|
| `javac` | Java Compiler | Converts `.java` source code → standard `.class` bytecode |
| `dx` / `d8` | Dalvik Cross-Assembler | Converts `.class` bytecode → `.dex` format understood by ART |
| `aapt` / `aapt2` | Android Asset Packaging Tool | Compiles XML resources, generates `R.java` (resource IDs), creates the APK |
| `apksigner` | APK Signer | Digitally signs the APK so Android trusts it |
| `zipalign` | ZIP Aligner | Optimizes the APK's structure for faster loading from storage |
| `adb` | Android Debug Bridge | Installs APKs, runs shell commands, streams logs |

### What is R.java?
`R.java` is an auto-generated file created by `aapt`. It contains integer IDs for every resource in your `res/` folder:
```java
public final class R {
    public static final class id {
        public static final int myButton = 0x7f080001;
        public static final int myTextView = 0x7f080002;
    }
    public static final class layout {
        public static final int activity_main = 0x7f030000;
    }
    public static final class string {
        public static final int app_name = 0x7f060000;
    }
}
```
This is why you write `R.id.myButton` in Java to reference the button you defined in XML.

---

## 2.5 Gradle — The Build Tool

**Gradle** is the build system Android Studio uses. It automates:
- Downloading dependencies (libraries from the internet)
- Compiling your code
- Running tests
- Packaging the APK

### build.gradle (App level) — Key Fields
```groovy
android {
    compileSdkVersion 34        // Compile against Android 14 APIs
    defaultConfig {
        applicationId "com.example.myapp"   // Unique package name
        minSdkVersion 21                    // Minimum: Android 5
        targetSdkVersion 34                 // Designed for Android 14
        versionCode 1                       // Integer version for Play Store
        versionName "1.0"                   // Human-readable version
    }
}

dependencies {
    implementation 'androidx.appcompat:appcompat:1.6.1'
    implementation 'com.google.android.material:material:1.11.0'
}
```

---

## 2.6 Android Emulator vs Real Device

| Feature | Emulator | Real Device |
|---------|----------|-------------|
| Cost | Free | Need a physical phone |
| Setup | Download via SDK Manager | Enable Developer Options + USB debugging |
| Speed | Slower (but hardware acceleration helps) | Fast |
| Camera, GPS | Simulated (limited) | Real hardware |
| Testing | Good for many screen sizes | Closest to real user experience |

### Enabling USB Debugging (Real Device)
1. Go to **Settings → About Phone**
2. Tap **Build Number** seven times → you are now a developer!
3. Go back → **Developer Options** appears
4. Enable **USB Debugging**
5. Connect via USB → click "Allow" on the phone

---

## 2.7 Key Terms Glossary (Topic 2)

| Term | Definition |
|------|------------|
| **ART** | Android Runtime — executes `.dex` bytecode on Android devices |
| **Dalvik** | The older runtime ART replaced; used JIT compilation |
| **AOT** | Ahead-of-Time compilation — compiles bytecode at install time for speed |
| **JIT** | Just-in-Time compilation — compiles bytecode at run time |
| **.dex** | Dalvik Executable — the bytecode format Android actually runs |
| **.apk** | Android Package — the installable file for Android apps |
| **aapt** | Android Asset Packaging Tool — packages resources into the APK |
| **ADB** | Android Debug Bridge — communicates with devices/emulators |
| **Gradle** | The build automation tool Android Studio uses |
| **R.java** | Auto-generated file that maps resource names to integer IDs |
| **Manifest** | `AndroidManifest.xml` — declares the app's components and permissions |

---

## 📝 Practice Questions — Topic 2

1. Draw and label the five layers of the Android architecture.
2. What is the difference between ART and the standard JVM?
3. Explain the steps in the Android build process. What tool converts `.class` to `.dex`?
4. What is `R.java` and how is it generated?
5. What is the purpose of `AndroidManifest.xml`?
6. Name three tools included in the Android SDK and state what each does.
7. What is the difference between `minSdkVersion` and `targetSdkVersion`?
8. What build system does Android Studio use, and what does it do?
