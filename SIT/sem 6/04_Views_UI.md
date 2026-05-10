# Topic 4 — Creating UI with Activity & Views

> **Syllabus hours:** 10 (largest topic!) &nbsp;|&nbsp; **Exam weight:** Very High

---

## 4.1 The View Class — Everything is a View

Every visible element on an Android screen is a **View**. The `android.view.View` class is the base class for ALL UI components.

```
android.view.View
 │
 ├── TextView
 │    └── EditText
 │         └── AutoCompleteTextView
 │
 ├── Button
 │    ├── CheckBox
 │    └── RadioButton
 │
 ├── ImageView
 │
 ├── ProgressBar
 │    ├── RatingBar
 │    └── SeekBar
 │
 └── ViewGroup  (invisible containers that hold other views)
      ├── LinearLayout
      ├── RelativeLayout
      ├── FrameLayout
      └── GridLayout
```

### Common Attributes (Inherited by ALL Views)

Every single view can use these XML attributes because they are defined on the base `View` class:

| Attribute | Values | Purpose |
|-----------|--------|---------|
| `android:id` | `"@+id/myView"` | Unique identifier so Java code can find this view |
| `android:layout_width` | `match_parent`, `wrap_content`, `Ndp` | How wide the view should be |
| `android:layout_height` | `match_parent`, `wrap_content`, `Ndp` | How tall the view should be |
| `android:padding` | `8dp`, `16dp` | Space INSIDE the view border |
| `android:margin` / `android:layout_margin` | `8dp` | Space OUTSIDE the view border |
| `android:background` | `"#FF0000"`, `@color/red` | Background colour |
| `android:visibility` | `visible`, `invisible`, `gone` | Whether the view is shown |
| `android:gravity` | `center`, `left`, `right`, `top`, `bottom` | Alignment of content INSIDE the view |

### match_parent vs wrap_content
```
┌─────────────────────────────────────────┐  ← Screen
│                                         │
│  ┌───────────────────────────────────┐  │
│  │  match_parent width button        │  │  ← Stretches to fill parent
│  └───────────────────────────────────┘  │
│                                         │
│  ┌─────────────┐                        │
│  │ wrap_content│                        │  ← Only as big as its content
│  └─────────────┘                        │
│                                         │
└─────────────────────────────────────────┘
```

### Referencing Views in Java

Use `findViewById()` to get a reference to a view defined in XML:

```java
// In XML: android:id="@+id/myButton"
Button myButton = (Button) findViewById(R.id.myButton);

// Shorter syntax with newer API (no cast needed):
Button myButton = findViewById(R.id.myButton);
```

---

## 4.2 dp and sp — The Right Units

Android screens come in many sizes and densities. Using pixels (px) directly would look huge on a low-res screen and tiny on a high-res screen.

| Unit | Full Name | Use For |
|------|-----------|---------|
| `dp` | Density-independent Pixels | All layout sizes — widths, heights, margins, padding |
| `sp` | Scale-independent Pixels | Font sizes only (also respects user's font size preference) |
| `px` | Pixels | Never use — differs per screen density |

> **Rule:** Sizes → `dp`. Text → `sp`. Never `px`.

---

## 4.3 TextView — Displaying Text

A `TextView` is the most basic widget. It displays a string of text that the user **cannot edit**.

### XML
```xml
<TextView
    android:id="@+id/myLabel"
    android:layout_width="wrap_content"
    android:layout_height="wrap_content"
    android:text="Hello, World!"
    android:textSize="18sp"
    android:textColor="#333333"
    android:textStyle="bold"
    android:gravity="center" />
```

### Key Attributes
| Attribute | Description |
|-----------|-------------|
| `android:text` | The text to display (use `@string/name` to reference strings.xml) |
| `android:textSize` | Font size, always in `sp` |
| `android:textColor` | Colour of the text (`#RRGGBB` or `@color/name`) |
| `android:textStyle` | `normal`, `bold`, `italic`, `bold\|italic` |
| `android:gravity` | Alignment of text within the view |
| `android:hint` | Greyed-out placeholder (only on EditText, but set here for reference) |

### Java — Reading and Setting Text
```java
TextView myLabel = findViewById(R.id.myLabel);

// Read the current text
String current = myLabel.getText().toString();

// Set new text
myLabel.setText("New text here");

// Set text from strings.xml resource
myLabel.setText(R.string.my_string);
```

---

## 4.4 EditText — User Text Input

`EditText` extends `TextView`. It is an **editable** input field.

### XML
```xml
<EditText
    android:id="@+id/nameInput"
    android:layout_width="match_parent"
    android:layout_height="wrap_content"
    android:hint="Enter your name"
    android:inputType="textPersonName" />
```

### The `inputType` Attribute — Very Important!

`inputType` controls which keyboard is shown and how input is treated:

| inputType Value | Effect |
|-----------------|--------|
| `text` | Default — plain text keyboard |
| `textPassword` | Masks input with dots; text keyboard |
| `number` | Numeric keyboard only (integers) |
| `numberDecimal` | Numeric keyboard with decimal point |
| `numberSigned` | Numbers with +/− sign |
| `phone` | Phone number keyboard |
| `textEmailAddress` | Text keyboard with @ symbol prominent |
| `textMultiLine` | Allows line breaks; shows multi-line input |
| `textCapSentences` | Auto-capitalises first letter of sentences |
| `textPersonName` | Plain text, optimised for names |

### Java — Reading EditText Input
```java
EditText nameInput = findViewById(R.id.nameInput);

// Read the text the user typed
String name = nameInput.getText().toString();

// Trim whitespace (good practice)
String trimmedName = nameInput.getText().toString().trim();

// Check if empty
if (name.isEmpty()) {
    nameInput.setError("Name cannot be empty");
}
```

### Validation
```java
public void onSubmitClicked(View view) {
    EditText emailInput = findViewById(R.id.emailInput);
    String email = emailInput.getText().toString().trim();

    if (email.isEmpty()) {
        emailInput.setError("Email is required");
        emailInput.requestFocus(); // move cursor here
        return;
    }
    // proceed...
}
```

---

## 4.5 Button — Tappable Action

A `Button` triggers an action when the user taps it.

### Method 1: XML onClick (Simpler — good for exam)
```xml
<Button
    android:id="@+id/submitBtn"
    android:layout_width="match_parent"
    android:layout_height="wrap_content"
    android:text="Submit"
    android:onClick="onSubmitClicked" />
```
```java
// In Activity — method name MUST match android:onClick exactly
public void onSubmitClicked(View view) {
    // This runs when the button is tapped
    Toast.makeText(this, "Button clicked!", Toast.LENGTH_SHORT).show();
}
```
> **Important rules for `android:onClick` method:**
> - Must be `public`
> - Must return `void`
> - Must take a single `View` parameter
> - Must exist in the Activity that uses this layout

### Method 2: setOnClickListener (More Flexible)
```java
Button submitBtn = findViewById(R.id.submitBtn);

submitBtn.setOnClickListener(new View.OnClickListener() {
    @Override
    public void onClick(View view) {
        // runs when tapped
        Log.d(TAG, "Button was tapped!");
    }
});
```

### Java 8 Lambda (Shorter Version of Method 2)
```java
submitBtn.setOnClickListener(view -> {
    Log.d(TAG, "Button was tapped!");
});
```

---

## 4.6 Toast — Quick Pop-up Messages

A **Toast** is a simple, temporary pop-up message. The user cannot interact with it — it just appears and disappears.

```java
// Short duration (about 2 seconds)
Toast.makeText(this, "Your message here", Toast.LENGTH_SHORT).show();

// Long duration (about 3.5 seconds)
Toast.makeText(this, "Your message here", Toast.LENGTH_LONG).show();
```

```
Toast.makeText(
    context,       ← 'this' = current Activity
    "message",     ← the text to show
    duration       ← Toast.LENGTH_SHORT or Toast.LENGTH_LONG
).show();          ← .show() is required or nothing appears!
```

> **Common mistake:** Forgetting `.show()` at the end. The toast will never display without it.

---

## 4.7 CheckBox — Multiple Selection

A `CheckBox` lets the user independently toggle an option on or off. Multiple checkboxes can be selected at the same time.

### XML
```xml
<CheckBox
    android:id="@+id/chkPizza"
    android:layout_width="wrap_content"
    android:layout_height="wrap_content"
    android:text="Pizza"
    android:checked="false" />

<CheckBox
    android:id="@+id/chkBurger"
    android:layout_width="wrap_content"
    android:layout_height="wrap_content"
    android:text="Burger" />
```

### Java — Reading CheckBox State
```java
CheckBox chkPizza  = findViewById(R.id.chkPizza);
CheckBox chkBurger = findViewById(R.id.chkBurger);

public void onOrderClicked(View view) {
    String order = "";
    if (chkPizza.isChecked())  { order += "Pizza ";  }
    if (chkBurger.isChecked()) { order += "Burger ";  }

    Toast.makeText(this, "Order: " + order, Toast.LENGTH_SHORT).show();
}
```

### Listening for Changes
```java
chkPizza.setOnCheckedChangeListener((checkBox, isChecked) -> {
    if (isChecked) {
        Log.d(TAG, "Pizza was selected");
    } else {
        Log.d(TAG, "Pizza was deselected");
    }
});
```

---

## 4.8 RadioButton & RadioGroup — Single Selection

`RadioButton` is used when the user must pick **exactly one** option from a group. RadioButtons MUST be placed inside a `<RadioGroup>` — without it, multiple radio buttons can be selected at the same time.

### XML
```xml
<RadioGroup
    android:id="@+id/sizeGroup"
    android:layout_width="wrap_content"
    android:layout_height="wrap_content"
    android:orientation="vertical">

    <RadioButton
        android:id="@+id/radioSmall"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:text="Small"
        android:checked="true" />   <!-- default selection -->

    <RadioButton
        android:id="@+id/radioMedium"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:text="Medium" />

    <RadioButton
        android:id="@+id/radioLarge"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:text="Large" />

</RadioGroup>
```

### Java — Reading RadioGroup Selection
```java
RadioGroup sizeGroup = findViewById(R.id.sizeGroup);

public void onOrderClicked(View view) {
    int selectedId = sizeGroup.getCheckedRadioButtonId();

    // getCheckedRadioButtonId() returns -1 if nothing is selected
    if (selectedId == -1) {
        Toast.makeText(this, "Please select a size", Toast.LENGTH_SHORT).show();
        return;
    }

    RadioButton selectedBtn = findViewById(selectedId);
    String selectedSize = selectedBtn.getText().toString();

    Toast.makeText(this, "Size: " + selectedSize, Toast.LENGTH_SHORT).show();
}
```

### Alternative: Using a Switch-Case
```java
switch (selectedId) {
    case R.id.radioSmall:
        // Small was chosen
        break;
    case R.id.radioMedium:
        // Medium was chosen
        break;
    case R.id.radioLarge:
        // Large was chosen
        break;
}
```

### CheckBox vs RadioButton — The Key Difference
```
CheckBox                         RadioButton (inside RadioGroup)
───────────────────              ──────────────────────────────────
☑ Option A   (selected)          ● Option A   (selected)
☑ Option B   (selected)          ○ Option B
☐ Option C   (not selected)      ○ Option C

Multiple can be selected          Only ONE can be selected at a time
Independence — each is its own   Grouped — selecting one deselects others
```

---

## 4.9 SeekBar — Draggable Slider

A `SeekBar` is a horizontal slider that lets the user pick a numeric value by dragging a thumb.

### XML
```xml
<SeekBar
    android:id="@+id/volumeSeek"
    android:layout_width="match_parent"
    android:layout_height="wrap_content"
    android:max="100"
    android:progress="50" />
```

### Key Attributes
| Attribute | Description |
|-----------|-------------|
| `android:max` | Maximum value (minimum is always 0) |
| `android:progress` | Starting value |

### Java — Listening to SeekBar Changes
```java
SeekBar volumeSeek = findViewById(R.id.volumeSeek);

volumeSeek.setOnSeekBarChangeListener(new SeekBar.OnSeekBarChangeListener() {

    @Override
    public void onProgressChanged(SeekBar seekBar, int progress, boolean fromUser) {
        // Called every time the thumb is dragged
        TextView label = findViewById(R.id.volumeLabel);
        label.setText("Volume: " + progress + "%");
    }

    @Override
    public void onStartTrackingTouch(SeekBar seekBar) {
        // User started dragging
    }

    @Override
    public void onStopTrackingTouch(SeekBar seekBar) {
        // User let go — use this for final value
        int finalValue = seekBar.getProgress();
        Log.d(TAG, "Final volume: " + finalValue);
    }
});

// Read current value at any time
int currentVolume = volumeSeek.getProgress();
```

---

## 4.10 RatingBar — Star Rating

A `RatingBar` lets the user tap on stars to give a rating.

### XML
```xml
<RatingBar
    android:id="@+id/myRating"
    android:layout_width="wrap_content"
    android:layout_height="wrap_content"
    android:numStars="5"
    android:rating="3.5"
    android:stepSize="0.5" />
```

### Key Attributes
| Attribute | Description |
|-----------|-------------|
| `android:numStars` | Total number of stars shown |
| `android:rating` | Starting rating value |
| `android:stepSize` | Granularity — `1` for whole stars, `0.5` for half stars |

### Java
```java
RatingBar myRating = findViewById(R.id.myRating);

// Read current rating
float rating = myRating.getRating();

// Listen for changes
myRating.setOnRatingBarChangeListener((ratingBar, rating2, fromUser) -> {
    Toast.makeText(this, "Rating: " + rating2 + " stars", Toast.LENGTH_SHORT).show();
});
```

---

## 4.11 Complete Example — A Simple Order Form

### activity_order.xml
```xml
<?xml version="1.0" encoding="utf-8"?>
<LinearLayout
    xmlns:android="http://schemas.android.com/apk/res/android"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    android:orientation="vertical"
    android:padding="16dp">

    <!-- Name input -->
    <TextView
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:text="Your Name:" />

    <EditText
        android:id="@+id/nameInput"
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:hint="Enter your name"
        android:inputType="textPersonName" />

    <!-- Size selection (only one) -->
    <TextView
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:text="Select Size:"
        android:layout_marginTop="16dp" />

    <RadioGroup
        android:id="@+id/sizeGroup"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content">

        <RadioButton android:id="@+id/radioSmall"
            android:layout_width="wrap_content"
            android:layout_height="wrap_content"
            android:text="Small" android:checked="true" />

        <RadioButton android:id="@+id/radioLarge"
            android:layout_width="wrap_content"
            android:layout_height="wrap_content"
            android:text="Large" />
    </RadioGroup>

    <!-- Extras (multiple) -->
    <TextView
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:text="Extras:"
        android:layout_marginTop="16dp" />

    <CheckBox android:id="@+id/chkCheese"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:text="Extra Cheese" />

    <CheckBox android:id="@+id/chkSauce"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:text="Extra Sauce" />

    <!-- Quantity slider -->
    <TextView android:id="@+id/qtyLabel"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:text="Quantity: 1"
        android:layout_marginTop="16dp" />

    <SeekBar android:id="@+id/qtySeek"
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:max="10"
        android:progress="1" />

    <!-- Rate us -->
    <RatingBar android:id="@+id/ratingBar"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:numStars="5"
        android:rating="3"
        android:stepSize="1"
        android:layout_marginTop="16dp" />

    <!-- Submit -->
    <Button
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:text="Place Order"
        android:onClick="onPlaceOrder"
        android:layout_marginTop="24dp" />

</LinearLayout>
```

### OrderActivity.java
```java
public class OrderActivity extends AppCompatActivity {

    private static final String TAG = "OrderActivity";

    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_order);

        // SeekBar listener — update label as user drags
        SeekBar qtySeek = findViewById(R.id.qtySeek);
        qtySeek.setOnSeekBarChangeListener(new SeekBar.OnSeekBarChangeListener() {
            @Override
            public void onProgressChanged(SeekBar seekBar, int progress, boolean fromUser) {
                TextView qtyLabel = findViewById(R.id.qtyLabel);
                qtyLabel.setText("Quantity: " + progress);
            }
            @Override public void onStartTrackingTouch(SeekBar seekBar) {}
            @Override public void onStopTrackingTouch(SeekBar seekBar) {}
        });
    }

    public void onPlaceOrder(View view) {
        // 1. Name
        EditText nameInput = findViewById(R.id.nameInput);
        String name = nameInput.getText().toString().trim();
        if (name.isEmpty()) {
            nameInput.setError("Name required");
            return;
        }

        // 2. Size
        RadioGroup sizeGroup = findViewById(R.id.sizeGroup);
        int sizeId = sizeGroup.getCheckedRadioButtonId();
        RadioButton sizeBtn = findViewById(sizeId);
        String size = sizeBtn.getText().toString();

        // 3. Extras
        CheckBox chkCheese = findViewById(R.id.chkCheese);
        CheckBox chkSauce  = findViewById(R.id.chkSauce);
        String extras = "";
        if (chkCheese.isChecked()) extras += "Cheese ";
        if (chkSauce.isChecked())  extras += "Sauce ";

        // 4. Quantity
        SeekBar qtySeek = findViewById(R.id.qtySeek);
        int qty = qtySeek.getProgress();

        // 5. Rating
        RatingBar ratingBar = findViewById(R.id.ratingBar);
        float rating = ratingBar.getRating();

        // Build summary
        String summary = name + " ordered " + qty + "x " + size
                + " pizza. Extras: " + extras + ". Rating: " + rating;
        Log.d(TAG, summary);
        Toast.makeText(this, "Order placed!", Toast.LENGTH_LONG).show();
    }
}
```

---

## 4.12 View Visibility

You can show or hide views dynamically:

```java
View myView = findViewById(R.id.myView);

// VISIBLE — shown, takes up space
myView.setVisibility(View.VISIBLE);

// INVISIBLE — hidden, but STILL TAKES UP SPACE (gap remains)
myView.setVisibility(View.INVISIBLE);

// GONE — hidden AND does NOT take up space (layout collapses)
myView.setVisibility(View.GONE);
```

---

## 4.13 Key Terms Glossary (Topic 4)

| Term | Definition |
|------|------------|
| **View** | The base class for all UI components in Android |
| **ViewGroup** | A View that contains other Views (layouts are ViewGroups) |
| **TextView** | A widget that displays non-editable text |
| **EditText** | A widget that allows the user to type text |
| **Button** | A tappable widget that triggers an action |
| **CheckBox** | A widget that can be independently checked or unchecked |
| **RadioButton** | A widget used in groups where only one can be selected |
| **RadioGroup** | A container that enforces single-selection among RadioButtons |
| **SeekBar** | A horizontal slider for selecting a value by dragging |
| **RatingBar** | A widget for selecting a star rating |
| **Toast** | A temporary pop-up message |
| **dp** | Density-independent Pixels — for layout sizes |
| **sp** | Scale-independent Pixels — for font sizes |
| **R.java** | Auto-generated file mapping resource names to integer IDs |
| **findViewById()** | Method to retrieve a View object by its ID |
| **isChecked()** | Method on CheckBox/RadioButton returning true if selected |
| **getProgress()** | Method on SeekBar returning the current slider value |
| **getRating()** | Method on RatingBar returning the current star rating |
| **getText().toString()** | Pattern for reading text from a TextView/EditText |

---

## 📝 Practice Questions — Topic 4

1. What class do all Android UI widgets inherit from?
2. What is the difference between `match_parent` and `wrap_content`?
3. Why should you use `sp` for text sizes instead of `dp` or `px`?
4. Write the XML for an `EditText` that only accepts a password (masked input).
5. Write the Java code to read the text from an `EditText` called `usernameInput`.
6. What are the three rules for a method to be used with `android:onClick`?
7. What is a `Toast`? Write the Java code to show one with a short duration.
8. What is the key difference between a `CheckBox` and a `RadioButton`? Why must RadioButtons be inside a `RadioGroup`?
9. Write the Java code to check if a CheckBox with id `chkTerms` is selected.
10. What method do you call on a `RadioGroup` to find which RadioButton is selected?
11. What does `setVisibility(View.GONE)` do? How is it different from `View.INVISIBLE`?
12. What does `getProgress()` return on a SeekBar with `max=100` when the user drags it to the middle?
