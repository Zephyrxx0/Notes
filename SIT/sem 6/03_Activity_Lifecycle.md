# Topic 3 — Building Blocks, Activity Lifecycle & LogCat

> **Syllabus hours:** 4 &nbsp;|&nbsp; **Exam weight:** Very High — lifecycle questions are almost always on exams

---

## 3.1 Building Blocks of Android

An Android app is assembled from **components** — independent, reusable pieces that the Android OS knows how to start and manage. There are four main component types:

```
 ┌──────────────────────────────────────────────────────────┐
 │              Android App Components                      │
 ├─────────────┬──────────────┬──────────────┬─────────────┤
 │  Activity   │   Service    │ Broadcast    │  Content    │
 │             │              │  Receiver    │  Provider   │
 │ Single UI   │ Background   │ Listen for   │ Share data  │
 │ screen      │ processing   │ system events│ across apps │
 └─────────────┴──────────────┴──────────────┴─────────────┘
```

### Activity (⭐ Most Important for Exam)
- Represents **one screen** the user can interact with
- Written as a Java class that **extends `AppCompatActivity`** (or `Activity`)
- Every activity has an associated **layout XML file** for its UI
- Declared in `AndroidManifest.xml`

```java
// A basic Activity skeleton
public class MainActivity extends AppCompatActivity {

    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_main); // link to XML layout
    }
}
```

### Service
- Runs **in the background without a UI**
- Examples: downloading a file, playing music, syncing data
- Keeps running even if the user switches to another app
- Example: A music player service keeps playing after you open Maps

### Broadcast Receiver
- Listens for **system-wide broadcast messages**
- Examples: "Battery is low", "SMS received", "Device booted", "WiFi connected"
- Your app can register to receive these events and react accordingly

### Content Provider
- A **standardised interface for sharing data** between apps
- Example: The Contacts app exposes a Content Provider so other apps can read contact names/numbers
- Accessed via a URI (like a web URL but for data)

---

## 3.2 Activity and Layout — The Dynamic Duo

Every screen you see is built from two files working together:

```
 ┌──────────────────────┐         ┌──────────────────────┐
 │  MainActivity.java   │ ──────▶ │ activity_main.xml    │
 │                      │         │                      │
 │  (Logic / Behaviour) │         │  (Appearance / UI)   │
 │                      │         │                      │
 │  • Handle clicks     │         │  • Button layout     │
 │  • Read user input   │         │  • Text positions    │
 │  • Calculate values  │         │  • Colors, sizes     │
 └──────────────────────┘         └──────────────────────┘
          Java                              XML
```

The activity says `setContentView(R.layout.activity_main)` to tell Android which XML layout to display.

### Intent — The Messenger
An **Intent** is an object used to:
1. **Start another Activity** (navigate to a new screen)
2. **Pass data** between activities
3. **Start a Service**
4. **Send a broadcast**

```java
// Starting a new Activity with an Intent
Intent intent = new Intent(this, SecondActivity.class);
intent.putExtra("message", "Hello from MainActivity!");
startActivity(intent);

// In SecondActivity, retrieving the data
Intent intent = getIntent();
String message = intent.getStringExtra("message");
```

---

## 3.3 The Activity Lifecycle

This is the most important diagram in Android development. Every activity goes through a predictable set of states managed by the Android OS.

### Why Does the Lifecycle Exist?
Android may need to reclaim memory or respond to interruptions (phone calls, the user switching apps). The OS notifies your activity through lifecycle callbacks so you can save data before being killed and restore it when you return.

### The Full Lifecycle Diagram

```
                    ┌─────────────────────┐
                    │  Activity Launched  │
                    └──────────┬──────────┘
                               │
                               ▼
                    ┌──────────────────────┐
          ┌────────▶│     onCreate()       │◀──────────────────┐
          │         │                      │                   │
          │         │  • Called ONCE when  │                   │
          │         │    activity is born  │                   │
          │         │  • setContentView()  │                   │
          │         │  • Initialize vars   │                   │
          │         └──────────┬───────────┘                   │
          │                    │                               │
          │                    ▼                               │
          │         ┌──────────────────────┐                   │
          │         │      onStart()       │◀───────┐          │
          │         │                      │        │          │
          │         │  • Activity VISIBLE  │        │          │
          │         │    but not focused   │        │          │
          │         └──────────┬───────────┘        │          │
          │                    │                    │          │
          │                    ▼                    │          │
          │         ┌──────────────────────┐        │          │
          │ ┌──────▶│     onResume()       │        │          │
          │ │       │                      │        │          │
          │ │       │  • Foreground,       │        │          │
          │ │       │    user CAN interact │        │          │
          │ │       └──────────┬───────────┘        │          │
          │ │                  │                    │          │
          │ │       ┌──────────▼───────────┐        │          │
          │ │       │   Activity RUNNING   │        │          │
          │ │       └──────────┬───────────┘        │          │
          │ │                  │                    │          │
          │ │       ┌──────────▼───────────┐        │          │
          │ │       │      onPause()       │        │          │
          │ │       │                      │        │          │
          │ │       │  • Partially hidden  │        │          │
          │ │       │  • SAVE quick state  │        │          │
          │ └───────│  • STOP animations   │        │          │
          │         └──────────┬───────────┘        │          │
          │                    │                    │          │
          │          ┌─────────▼──────────┐         │          │
          │          │    onStop()        │─────────┘          │
          │          │                   │ onRestart()         │
          │          │  • Fully HIDDEN   │ (user comes back)   │
          │          │  • Release heavy  │                     │
          │          │    resources      │                     │
          │          └─────────┬─────────┘                     │
          │                    │                               │
          │          ┌─────────▼──────────┐                    │
          └──────────│   onDestroy()      │                    │
                     │                   │────────────────────┘
                     │  • Activity is    │  (Activity recreated,
                     │    about to die   │   e.g. screen rotate)
                     │  • Final cleanup  │
                     └─────────┬─────────┘
                               │
                     ┌─────────▼──────────┐
                     │  Activity Destroyed │
                     └────────────────────┘
```

### Lifecycle Methods — When to Use Each

| Method | When Called | What to Do Here |
|--------|------------|----------------|
| `onCreate()` | Activity first created | `setContentView()`, initialize variables, set up listeners |
| `onStart()` | Activity becomes visible | Register receivers, refresh UI data |
| `onResume()` | Activity gains focus (foreground) | Start animations, open camera, resume timers |
| `onPause()` | Activity partially hidden | **Save data**, pause animations, release camera |
| `onStop()` | Activity fully hidden | Release heavy resources, stop network calls |
| `onRestart()` | Activity coming back after `onStop()` | Refresh data before becoming visible again |
| `onDestroy()` | Activity being destroyed | Release all resources, final cleanup |

### The Three Key Pairs

```
onCreate()  ←→  onDestroy()    Entire lifetime
onStart()   ←→  onStop()       Visible lifetime
onResume()  ←→  onPause()      Foreground (interactive) lifetime
```

---

## 3.4 Lifecycle Scenarios — What Actually Happens

### Scenario 1: Normal App Launch
```
App starts → onCreate() → onStart() → onResume() → [User uses app]
```

### Scenario 2: Home Button Pressed
```
[User uses app] → onPause() → onStop()
[User returns]  → onRestart() → onStart() → onResume()
```

### Scenario 3: Back Button Pressed
```
[User uses app] → onPause() → onStop() → onDestroy()
```

### Scenario 4: Phone Call Interruption
```
[App running] → onPause() → onStop()
[Call ends]   → onRestart() → onStart() → onResume()
```

### Scenario 5: Screen Rotation
```
[App running] → onPause() → onStop() → onDestroy()
              → onCreate() → onStart() → onResume()
```
> **Important!** Rotating the screen **destroys and recreates** the activity. Any data stored in instance variables is lost! Use `onSaveInstanceState()` to preserve data.

### Saving State Across Rotation
```java
// Save data BEFORE the activity is destroyed
@Override
protected void onSaveInstanceState(Bundle outState) {
    super.onSaveInstanceState(outState);
    outState.putInt("seconds", seconds);
    outState.putBoolean("running", running);
}

// Restore data AFTER the activity is recreated
@Override
protected void onCreate(Bundle savedInstanceState) {
    super.onCreate(savedInstanceState);
    setContentView(R.layout.activity_main);

    if (savedInstanceState != null) {
        seconds = savedInstanceState.getInt("seconds");
        running = savedInstanceState.getBoolean("running");
    }
}
```

---

## 3.5 A Complete Activity Example (Stopwatch)

```java
public class StopwatchActivity extends AppCompatActivity {

    private int seconds = 0;
    private boolean running = false;

    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_stopwatch);

        // Restore state if activity was recreated (e.g. screen rotation)
        if (savedInstanceState != null) {
            seconds = savedInstanceState.getInt("seconds");
            running = savedInstanceState.getBoolean("running");
        }
        runTimer();
    }

    // Called when Start button is clicked (set in XML: android:onClick="onClickStart")
    public void onClickStart(View view) { running = true; }

    // Called when Stop button is clicked
    public void onClickStop(View view) { running = false; }

    // Called when Reset button is clicked
    public void onClickReset(View view) {
        running = false;
        seconds = 0;
    }

    // Runs a timer that updates the TextView every second
    private void runTimer() {
        final TextView timeView = (TextView) findViewById(R.id.time_view);
        final Handler handler = new Handler();

        handler.post(new Runnable() {
            @Override
            public void run() {
                int hours   = seconds / 3600;
                int minutes = (seconds % 3600) / 60;
                int secs    = seconds % 60;
                String time = String.format("%d:%02d:%02d", hours, minutes, secs);
                timeView.setText(time);
                if (running) { seconds++; }
                handler.postDelayed(this, 1000); // repeat every 1 second
            }
        });
    }

    @Override
    protected void onSaveInstanceState(Bundle outState) {
        super.onSaveInstanceState(outState);
        outState.putInt("seconds", seconds);
        outState.putBoolean("running", running);
    }
}
```

---

## 3.6 LogCat — Your Debugging Friend

**LogCat** is Android's logging system. It shows real-time output from the OS and your app in Android Studio's **Logcat** window (bottom panel).

### Log Class Methods

```java
import android.util.Log;

// Log.methodName(TAG, message)
Log.v("MyApp", "Verbose: lots of detail, lowest priority");
Log.d("MyApp", "Debug: useful during development");
Log.i("MyApp", "Info: general information");
Log.w("MyApp", "Warning: something unexpected happened");
Log.e("MyApp", "Error: something went wrong!");
```

### Priority Levels (lowest → highest)
```
VERBOSE  (V)  → Most detail, use during heavy debugging
DEBUG    (D)  → Development info, removed for release
INFO     (I)  → General informational messages
WARN     (W)  → Non-fatal unexpected situations
ERROR    (E)  → Errors — always check these!
ASSERT   (A)  → Fatal errors — should never happen
```

> **Rule of thumb:** Use `Log.d()` while building. In production (released app), only `Log.e()` and `Log.w()` should remain.

### Using a TAG Constant (Best Practice)
```java
public class MainActivity extends AppCompatActivity {

    // Define a TAG constant — use the class name for easy filtering
    private static final String TAG = "MainActivity";

    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_main);

        Log.d(TAG, "onCreate() called");
    }

    @Override
    protected void onResume() {
        super.onResume();
        Log.d(TAG, "onResume() called - activity is now interactive");
    }
}
```

### Reading LogCat Output
```
2024-01-15 10:23:45.123  1234-1234/com.example.myapp D/MainActivity: onCreate() called
│           │             │           │               │ │              │
│           │             │           │               │ │              └── Your message
│           │             │           │               │ └── Your TAG
│           │             │           │               └── Priority level (D=Debug)
│           │             │           └── App package name
│           │             └── Process ID / Thread ID
│           └── Timestamp
└── Date
```

### Filtering LogCat
In Android Studio's Logcat panel, you can filter by:
- **Package name** — see only your app's logs
- **Tag** — see only logs with a specific tag
- **Log level** — e.g., "Debug and above" hides Verbose

---

## 3.7 Key Terms Glossary (Topic 3)

| Term | Definition |
|------|------------|
| **Activity** | A single screen with a user interface |
| **Intent** | A message object used to start activities or pass data |
| **Service** | A component that runs background tasks without a UI |
| **Broadcast Receiver** | A component that listens for system-wide events |
| **Content Provider** | A component that shares data between apps |
| **Lifecycle** | The sequence of states an Activity goes through from creation to destruction |
| **Bundle** | A key-value storage object used to pass data between activities and save state |
| **LogCat** | Android's logging system; viewed in Android Studio's Logcat window |
| **onSaveInstanceState** | Method to save data before the activity is destroyed |
| **setContentView()** | Links an activity to its XML layout |

---

## 📝 Practice Questions — Topic 3

1. List the four building blocks of Android and briefly describe each.
2. Draw the complete Activity lifecycle diagram with all method names.
3. What happens to an Activity when the user presses the Home button? Trace through the lifecycle.
4. Why is `onSaveInstanceState()` important? When is it called?
5. What is the difference between `onPause()` and `onStop()`?
6. What will happen to a running stopwatch app when the screen is rotated? How do you fix it?
7. Write the five `Log` methods in order of priority (lowest to highest).
8. What is an Intent? Give two uses of an Intent.
9. In what lifecycle method should you call `setContentView()`?
10. What does a `TAG` string do in LogCat?
