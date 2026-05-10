# Topic 1 — Mobile Application Development & Frameworks

> **Syllabus hours:** 6 &nbsp;|&nbsp; **Exam weight:** Moderate

---

## 1.1 What is Mobile Application Development?

Mobile application development is the process of creating software that runs on mobile devices like smartphones and tablets. Unlike desktop apps, mobile apps must deal with:

- **Limited battery** — minimize CPU and network usage
- **Varying screen sizes** — phones, tablets, foldables
- **Intermittent connectivity** — apps must work offline or degrade gracefully
- **Touch-first interaction** — no mouse, everything is a tap or swipe
- **Device permissions** — camera, GPS, contacts must be explicitly requested

### Types of Mobile Apps

| Type | Description | Examples |
|------|-------------|---------|
| **Native App** | Written for one specific platform using its own SDK | Android app in Java/Kotlin |
| **Web App** | A website that looks like an app (runs in browser) | Mobile-friendly website |
| **Hybrid App** | Wraps web code inside a native shell | Ionic apps |
| **Cross-Platform** | One codebase, compiles to multiple native platforms | Flutter, React Native |

---

## 1.2 Mobile Platforms Overview

### Major Platforms
| Platform | Owner | Language(s) | Market Share |
|----------|-------|------------|--------------|
| **Android** | Google | Java, Kotlin | ~72% global |
| **iOS** | Apple | Swift, Objective-C | ~27% global |
| **Windows Phone** | Microsoft | C# | Discontinued |

> **Exam note:** Android dominates the global market because it is open-source and runs on hardware from many manufacturers.

---

## 1.3 Application Development Frameworks

A **framework** is a structured collection of pre-written code, tools, and conventions that guides how you build an app. Instead of writing everything from scratch, you follow the framework's rules and fill in the logic specific to your app.

### Native Android Framework
- **Language:** Java (or Kotlin)
- **Tool:** Android Studio
- **SDK:** Android SDK (Software Development Kit)
- **Best for:** Full access to all device features, best performance
- **What you learn in T3373**

### Apache Cordova / PhoneGap
- **Language:** HTML, CSS, JavaScript
- **How it works:** Renders your web app inside a hidden browser (WebView)
- **Limitation:** Slower than native; limited access to hardware

### React Native (by Facebook/Meta)
- **Language:** JavaScript + React
- **How it works:** JavaScript code is bridged to real native UI components
- **Advantage:** Faster than Cordova; still cross-platform

### Flutter (by Google)
- **Language:** Dart
- **How it works:** Has its own rendering engine — draws every pixel itself
- **Advantage:** Very consistent look across platforms

### Xamarin (by Microsoft)
- **Language:** C# / .NET
- **How it works:** Compiles to native code for Android and iOS
- **Advantage:** Good for teams already working in C#

### Framework Comparison Diagram
```
                       Native vs Cross-Platform

 NATIVE                          CROSS-PLATFORM
 ┌────────────────┐               ┌─────────────────────┐
 │ Android (Java) │               │ Flutter (Dart)       │
 │                │               │ React Native (JS)    │
 │  Full device   │               │ Ionic (HTML/JS/CSS)  │
 │  access        │               │ Xamarin (C#)         │
 │  Best perf.    │               │                      │
 │  One platform  │               │  One codebase        │
 │  only          │               │  Slightly slower     │
 └────────────────┘               └─────────────────────┘

  High Control ◄────────────────────────────► High Portability
```

---

## 1.4 Why Android?

Android was chosen for this course for several practical reasons:

1. **Open Source** — Anyone can see, modify, and distribute the source code (AOSP — Android Open Source Project)
2. **Market share** — More than 70% of smartphones worldwide run Android
3. **Java** — You already know Java (pre-requisite); Android apps use Java
4. **Free tools** — Android Studio is free; no Mac required (unlike iOS development)
5. **Easy distribution** — You can install your own APK on your own phone for free (sideloading), unlike iOS

---

## 1.5 Android Versions & API Levels

Android has many versions, each with a dessert codename and an **API level** number. The API level is the most important number — it tells you which features are available.

```
Version    Codename              API Level
──────────────────────────────────────────────
1.5        Cupcake               3
1.6        Donut                 4
2.3        Gingerbread           9–10
4.0        Ice Cream Sandwich    14–15
4.1–4.3    Jelly Bean            16–18
4.4        KitKat                19–20     ← Common minimum target
5.0–5.1    Lollipop              21–22
6.0        Marshmallow           23
7.0–7.1    Nougat                24–25
8.0–8.1    Oreo                  26–27
9          Pie                   28
10         Q / Android 10        29
11         R / Android 11        30
12         S / Android 12        31
13         T / Android 13        33
14         U / Android 14        34
```

### Minimum SDK vs. Target SDK vs. Compile SDK
| Attribute | Meaning |
|-----------|---------|
| `minSdkVersion` | Oldest Android your app supports; it **won't install** on older devices |
| `targetSdkVersion` | The version you designed and tested against |
| `compileSdkVersion` | The API version Android Studio uses to compile your code |

> **Practical tip:** Setting `minSdk = 19` (KitKat) lets your app run on the vast majority of devices still in use.

---

## 1.6 Key Terms Glossary (Topic 1)

| Term | Definition |
|------|------------|
| **SDK** | Software Development Kit — a collection of tools, libraries, and documentation for building apps |
| **APK** | Android Package — the installable file format for Android apps (like a `.exe` on Windows) |
| **Native app** | An app built with the platform's own language and tools |
| **Framework** | A structured set of reusable code that guides how you build an app |
| **API Level** | An integer that identifies the version of the Android platform's APIs |
| **AOSP** | Android Open Source Project — the open-source core of Android |

---

## 📝 Practice Questions — Topic 1

1. What is the difference between a native app and a hybrid app?
2. Name three cross-platform mobile development frameworks and state the language each uses.
3. What is an API level, and why is `minSdkVersion` important?
4. List three advantages of Android over iOS from a developer's perspective.
5. What does "open source" mean in the context of Android?
