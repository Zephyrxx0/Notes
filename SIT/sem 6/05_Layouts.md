# Topic 5 — Layouts

> **Syllabus hours:** 4 &nbsp;|&nbsp; **Exam weight:** High — expect XML questions and diagrams

---

## 5.1 What is a Layout?

A **layout** is a special type of View called a **ViewGroup** (`android.view.ViewGroup`). It is an invisible container that holds and arranges other Views on the screen.

```
 ViewGroup (Layout — invisible container)
 ┌──────────────────────────────────────────┐
 │  ┌─────────────┐   ┌──────────────────┐  │
 │  │  TextView   │   │     Button       │  │
 │  └─────────────┘   └──────────────────┘  │
 │       View                View           │
 └──────────────────────────────────────────┘
```

Layouts determine:
- **Where** children are placed (top-left? stacked? in a grid?)
- **How big** children are allowed to be
- How children relate to each other

---

## 5.2 LinearLayout — Row or Column

`LinearLayout` places all its children in **a single row or a single column** — never both at the same time.

### Orientation: Vertical (Column)
```xml
<LinearLayout
    xmlns:android="http://schemas.android.com/apk/res/android"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    android:orientation="vertical"
    android:padding="16dp">

    <TextView
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:text="First (Top)" />

    <TextView
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:text="Second (Middle)" />

    <TextView
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:text="Third (Bottom)" />

</LinearLayout>
```
```
 ┌─────────────────────────────┐
 │ First (Top)                 │
 ├─────────────────────────────┤
 │ Second (Middle)             │
 ├─────────────────────────────┤
 │ Third (Bottom)              │
 └─────────────────────────────┘
```

### Orientation: Horizontal (Row)
```xml
<LinearLayout
    android:layout_width="match_parent"
    android:layout_height="wrap_content"
    android:orientation="horizontal">

    <Button android:layout_width="wrap_content"
            android:layout_height="wrap_content"
            android:text="Yes" />

    <Button android:layout_width="wrap_content"
            android:layout_height="wrap_content"
            android:text="No" />

    <Button android:layout_width="wrap_content"
            android:layout_height="wrap_content"
            android:text="Cancel" />

</LinearLayout>
```
```
 ┌────────┬──────┬──────────┐
 │  Yes   │  No  │  Cancel  │
 └────────┴──────┴──────────┘
```

### layout_weight — Sharing Space Proportionally

`layout_weight` lets children share available space in a ratio. Set `layout_width="0dp"` (or `layout_height="0dp"` for vertical) when using weight:

```xml
<LinearLayout
    android:layout_width="match_parent"
    android:layout_height="wrap_content"
    android:orientation="horizontal">

    <Button android:layout_width="0dp"
            android:layout_height="wrap_content"
            android:layout_weight="1"
            android:text="Left 1/3" />

    <Button android:layout_width="0dp"
            android:layout_height="wrap_content"
            android:layout_weight="2"
            android:text="Right 2/3" />

</LinearLayout>
```
```
 ┌──────────────┬────────────────────────────┐
 │   Left 1/3   │       Right 2/3            │
 └──────────────┴────────────────────────────┘
  ◄──── 1 ────► ◄──────────── 2 ────────────►
```

### Nesting LinearLayouts (for complex UIs)
```xml
<!-- Row + Column combination -->
<LinearLayout android:orientation="vertical">

    <LinearLayout android:orientation="horizontal">
        <EditText ... android:hint="First name" android:layout_weight="1"/>
        <EditText ... android:hint="Last name"  android:layout_weight="1"/>
    </LinearLayout>

    <Button android:text="Submit" />

</LinearLayout>
```
```
 ┌──────────────────┬──────────────────┐
 │   First name     │   Last name      │   ← horizontal inner layout
 └──────────────────┴──────────────────┘
 ┌────────────────────────────────────┐
 │              Submit                │   ← vertical outer layout
 └────────────────────────────────────┘
```

> **Caution:** Deep nesting of LinearLayouts slows down your app. For complex UIs, use ConstraintLayout instead (see section 5.7).

---

## 5.3 RelativeLayout — Position Relative to Others

`RelativeLayout` lets you position each child **relative to the parent** or **relative to another view** in the layout. This makes complex UIs possible without nesting.

### Positioning Relative to Parent
```xml
<RelativeLayout
    android:layout_width="match_parent"
    android:layout_height="match_parent">

    <!-- Top-left corner of parent -->
    <TextView android:id="@+id/topLeft"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:text="Top Left"
        android:layout_alignParentTop="true"
        android:layout_alignParentLeft="true" />

    <!-- Bottom-right corner of parent -->
    <Button android:id="@+id/bottomRight"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:text="Bottom Right"
        android:layout_alignParentBottom="true"
        android:layout_alignParentRight="true" />

    <!-- Centred in parent -->
    <TextView android:id="@+id/centred"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:text="Centre"
        android:layout_centerInParent="true" />

</RelativeLayout>
```
```
 ┌────────────────────────────────┐
 │ Top Left                       │
 │                                │
 │           Centre               │
 │                                │
 │                   Bottom Right │
 └────────────────────────────────┘
```

### Positioning Relative to Another View

Use the **ID** of the other view as the reference:

```xml
<RelativeLayout
    android:layout_width="match_parent"
    android:layout_height="match_parent">

    <EditText
        android:id="@+id/emailInput"
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:hint="Email"
        android:layout_alignParentTop="true" />

    <!-- This button appears BELOW emailInput -->
    <Button
        android:id="@+id/loginBtn"
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:text="Login"
        android:layout_below="@id/emailInput" />

    <!-- This text appears TO THE RIGHT OF loginBtn -->
    <TextView
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:text="Forgot password?"
        android:layout_toRightOf="@id/loginBtn"
        android:layout_below="@id/emailInput" />

</RelativeLayout>
```

### All RelativeLayout Attributes

**Relative to Parent:**
| Attribute | Description |
|-----------|-------------|
| `android:layout_alignParentTop="true"` | Aligns top edge to parent's top |
| `android:layout_alignParentBottom="true"` | Aligns bottom edge to parent's bottom |
| `android:layout_alignParentLeft="true"` | Aligns left edge to parent's left |
| `android:layout_alignParentRight="true"` | Aligns right edge to parent's right |
| `android:layout_centerInParent="true"` | Centres both horizontally and vertically |
| `android:layout_centerHorizontal="true"` | Centres horizontally only |
| `android:layout_centerVertical="true"` | Centres vertically only |

**Relative to Another View (use `@id/targetViewId`):**
| Attribute | Description |
|-----------|-------------|
| `android:layout_above="@id/view"` | Positions this view ABOVE the referenced view |
| `android:layout_below="@id/view"` | Positions this view BELOW the referenced view |
| `android:layout_toLeftOf="@id/view"` | Positions this view to the LEFT of the referenced view |
| `android:layout_toRightOf="@id/view"` | Positions this view to the RIGHT of the referenced view |
| `android:layout_alignTop="@id/view"` | Aligns this view's TOP edge with the referenced view's top |
| `android:layout_alignBottom="@id/view"` | Aligns bottom edges |
| `android:layout_alignLeft="@id/view"` | Aligns left edges |
| `android:layout_alignRight="@id/view"` | Aligns right edges |

---

## 5.4 FrameLayout — Stacking Views

`FrameLayout` is designed to **stack views on top of each other**. The first child is at the bottom of the stack; each subsequent child is drawn on top.

```
 FrameLayout
 ┌─────────────────────────────────────┐
 │  ┌───────────────────────────────┐  │
 │  │  ImageView (background image) │  │  ← Layer 1 (bottom)
 │  │  ┌──────────────────────┐     │  │
 │  │  │  TextView (caption)  │     │  │  ← Layer 2 (on top)
 │  │  └──────────────────────┘     │  │
 │  └───────────────────────────────┘  │
 └─────────────────────────────────────┘
```

### XML — Image with Text Overlay
```xml
<FrameLayout
    android:layout_width="match_parent"
    android:layout_height="200dp">

    <!-- Layer 1: background image -->
    <ImageView
        android:layout_width="match_parent"
        android:layout_height="match_parent"
        android:src="@drawable/mountain"
        android:scaleType="centerCrop" />

    <!-- Layer 2: text on top of the image -->
    <TextView
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:text="Beautiful Mountain"
        android:textColor="#FFFFFF"
        android:textSize="20sp"
        android:layout_gravity="bottom|center_horizontal"
        android:padding="8dp" />

</FrameLayout>
```

### When to Use FrameLayout
- Placing text/badge over an image
- Tab content area where only one fragment is shown at a time
- **Hosting Fragments** — a common pattern is an empty `FrameLayout` acting as a container that Fragments are swapped in and out of

> **Note:** `layout_gravity` (not `android:gravity`) positions a child WITHIN the FrameLayout.

---

## 5.5 GridLayout — Rows and Columns

`GridLayout` splits the screen into a grid of **rows and columns**. You assign each child to a specific cell.

### XML
```xml
<GridLayout
    xmlns:android="http://schemas.android.com/apk/res/android"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    android:columnCount="3"
    android:rowCount="2">

    <!-- Row 0, Col 0 -->
    <Button
        android:text="1"
        android:layout_row="0"
        android:layout_column="0" />

    <!-- Row 0, Col 1 -->
    <Button
        android:text="2"
        android:layout_row="0"
        android:layout_column="1" />

    <!-- Row 0, Col 2 -->
    <Button
        android:text="3"
        android:layout_row="0"
        android:layout_column="2" />

    <!-- Row 1, Col 0 — spans 3 columns! -->
    <Button
        android:text="Span All"
        android:layout_row="1"
        android:layout_column="0"
        android:layout_columnSpan="3"
        android:layout_gravity="fill_horizontal" />

</GridLayout>
```

```
 ┌──────────┬──────────┬──────────┐
 │    1     │    2     │    3     │  ← Row 0
 ├──────────┴──────────┴──────────┤
 │          Span All              │  ← Row 1 (spans all 3 columns)
 └────────────────────────────────┘
```

### GridLayout Attributes
| Attribute | Applies To | Description |
|-----------|-----------|-------------|
| `android:columnCount` | GridLayout | Total number of columns |
| `android:rowCount` | GridLayout | Total number of rows |
| `android:layout_row` | Child | Which row this child goes in (0-indexed) |
| `android:layout_column` | Child | Which column this child goes in (0-indexed) |
| `android:layout_columnSpan` | Child | How many columns this child spans |
| `android:layout_rowSpan` | Child | How many rows this child spans |
| `android:layout_gravity` | Child | Alignment within its cell |

---

## 5.6 ScrollView — Making Content Scrollable

Standard layouts do **not** scroll automatically. If your content is taller than the screen, anything below the fold is simply cut off. Wrap the layout in a `<ScrollView>` to fix this.

> **Rule:** `ScrollView` can only have **ONE direct child**. That child is usually a `LinearLayout` that contains all your scrollable content.

### XML — Vertical Scrolling
```xml
<ScrollView
    xmlns:android="http://schemas.android.com/apk/res/android"
    android:layout_width="match_parent"
    android:layout_height="match_parent">

    <!-- ScrollView can only have ONE child -->
    <LinearLayout
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:orientation="vertical"
        android:padding="16dp">

        <TextView ... />
        <EditText ... />
        <Button   ... />
        <!-- ... many more views ... -->
        <TextView android:text="Way down here!" ... />

    </LinearLayout>

</ScrollView>
```

```
Screen viewport        Actual content (taller than screen)
 ┌───────────────┐     ┌───────────────┐
 │  TextView     │     │  TextView     │
 │               │     │               │
 │  EditText     │     │  EditText     │
 │               │     │               │
 │  Button       │     │  Button       │
 │               │     │               │
 └───────────────┘     │  More views   │
   ↕ can scroll        │               │
                       │  Way down here│
                       └───────────────┘
```

### Horizontal Scrolling
```xml
<HorizontalScrollView
    android:layout_width="match_parent"
    android:layout_height="wrap_content">

    <LinearLayout
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:orientation="horizontal">

        <!-- Many wide views side by side -->

    </LinearLayout>

</HorizontalScrollView>
```

---

## 5.7 Tangent — ConstraintLayout (Modern Best Practice)

Although not explicitly on your syllabus, **ConstraintLayout** is the default layout in all new Android Studio projects and is heavily featured in the Head First Android book. Understanding it helps you understand the IDE.

### Why ConstraintLayout?
- Replaces the need to **nest layouts** — keeps the view hierarchy **flat**
- A flat hierarchy means Android has less to measure and draw → **faster rendering**
- Built-in to the visual Design editor in Android Studio (the "Blueprint" view)

### How Constraints Work
Each view is connected to other views or to the parent using **constraints** (like springs). A view must have at least one horizontal and one vertical constraint, or it defaults to position (0,0).

```xml
<androidx.constraintlayout.widget.ConstraintLayout
    android:layout_width="match_parent"
    android:layout_height="match_parent">

    <Button
        android:id="@+id/myButton"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:text="Click Me"
        app:layout_constraintTop_toTopOf="parent"
        app:layout_constraintBottom_toBottomOf="parent"
        app:layout_constraintLeft_toLeftOf="parent"
        app:layout_constraintRight_toRightOf="parent" />
        <!-- ↑ This button is constrained to all four edges = centred -->

</androidx.constraintlayout.widget.ConstraintLayout>
```

### ConstraintLayout vs Nested LinearLayouts
```
With Nested LinearLayouts:           With ConstraintLayout:
─────────────────────────────        ──────────────────────────────────
LinearLayout (vertical)              ConstraintLayout
  └─ LinearLayout (horizontal)         ├─ TextView
       ├─ TextView                      ├─ EditText
       └─ EditText                      └─ Button
  └─ Button
                                      FLAT hierarchy — faster!
Depth: 3 levels
```

---

## 5.8 Choosing the Right Layout

Use this decision guide when picking a layout:

```
What do I need?
 │
 ├─ Simple column or row of views?
 │   └── LinearLayout (orientation="vertical" or "horizontal")
 │
 ├─ Position views relative to each other or the screen edge?
 │   └── RelativeLayout
 │
 ├─ Stack views on top of each other (image + text overlay)?
 │   └── FrameLayout
 │
 ├─ Rows and columns like a table or keypad?
 │   └── GridLayout
 │
 ├─ Content that might be taller than the screen?
 │   └── Wrap existing layout in ScrollView
 │
 └─ Complex UI with many views and constraints between them?
     └── ConstraintLayout (modern, best performance)
```

---

## 5.9 Layout XML — Essential Patterns

### Setting Padding and Margin
```xml
<!-- Uniform padding on all sides -->
<LinearLayout android:padding="16dp" ...>

<!-- Padding on individual sides -->
<TextView
    android:paddingTop="8dp"
    android:paddingBottom="8dp"
    android:paddingLeft="16dp"
    android:paddingRight="16dp" />

<!-- Margin (space OUTSIDE the view) -->
<Button
    android:layout_margin="8dp"
    android:layout_marginTop="16dp" />
```

### Difference: Padding vs Margin
```
 ─ ─ ─ ─ ─ ─ ─ ─ ─ ─ ─ ─ ─ ─ ─ ─ ─ ─ ─ ─
│          MARGIN (space outside border)    │
│   ╔══════════════════════════════════╗   │
│   ║   PADDING (space inside border) ║   │
│   ║   ┌──────────────────────────┐  ║   │
│   ║   │       CONTENT            │  ║   │
│   ║   └──────────────────────────┘  ║   │
│   ╚══════════════════════════════════╝   │
 ─ ─ ─ ─ ─ ─ ─ ─ ─ ─ ─ ─ ─ ─ ─ ─ ─ ─ ─ ─
```

### gravity vs layout_gravity
| Attribute | Controls | Use on |
|-----------|---------|--------|
| `android:gravity` | Alignment of content **inside** the view | Any View |
| `android:layout_gravity` | Where the view places **itself** within its parent | Child of FrameLayout or LinearLayout |

```xml
<!-- Text is centred INSIDE the button -->
<Button android:gravity="center" android:text="OK" />

<!-- The button itself is placed to the RIGHT inside a FrameLayout -->
<Button android:layout_gravity="end" android:text="OK" />
```

---

## 5.10 Complete Example — Login Screen

### activity_login.xml using RelativeLayout
```xml
<?xml version="1.0" encoding="utf-8"?>
<RelativeLayout
    xmlns:android="http://schemas.android.com/apk/res/android"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    android:padding="24dp">

    <!-- App title centred at top -->
    <TextView
        android:id="@+id/titleText"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:text="Welcome Back"
        android:textSize="28sp"
        android:textStyle="bold"
        android:layout_centerHorizontal="true"
        android:layout_alignParentTop="true"
        android:layout_marginTop="48dp" />

    <!-- Email input, below the title -->
    <EditText
        android:id="@+id/emailInput"
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:hint="Email address"
        android:inputType="textEmailAddress"
        android:layout_below="@id/titleText"
        android:layout_marginTop="32dp" />

    <!-- Password input, below email -->
    <EditText
        android:id="@+id/passwordInput"
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:hint="Password"
        android:inputType="textPassword"
        android:layout_below="@id/emailInput"
        android:layout_marginTop="16dp" />

    <!-- Login button, below password -->
    <Button
        android:id="@+id/loginBtn"
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:text="Log In"
        android:onClick="onLoginClicked"
        android:layout_below="@id/passwordInput"
        android:layout_marginTop="24dp" />

    <!-- "Forgot password" link, to the right of login button at same level -->
    <TextView
        android:id="@+id/forgotText"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:text="Forgot password?"
        android:layout_below="@id/loginBtn"
        android:layout_centerHorizontal="true"
        android:layout_marginTop="16dp" />

    <!-- Register link at the very bottom -->
    <TextView
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:text="Don't have an account? Register"
        android:layout_alignParentBottom="true"
        android:layout_centerHorizontal="true"
        android:layout_marginBottom="16dp" />

</RelativeLayout>
```

---

## 5.11 Key Terms Glossary (Topic 5)

| Term | Definition |
|------|------------|
| **ViewGroup** | A View that contains and arranges other Views (all layouts are ViewGroups) |
| **LinearLayout** | Places children in a single horizontal or vertical line |
| **RelativeLayout** | Positions children relative to the parent or to other children |
| **FrameLayout** | Stacks children on top of each other |
| **GridLayout** | Places children in a grid of rows and columns |
| **ScrollView** | Wraps content to enable vertical scrolling |
| **HorizontalScrollView** | Wraps content to enable horizontal scrolling |
| **ConstraintLayout** | Modern, flat layout using constraints between views |
| **orientation** | `LinearLayout` attribute: `"vertical"` or `"horizontal"` |
| **layout_weight** | `LinearLayout` attribute: defines proportional space sharing |
| **layout_below** | `RelativeLayout` attribute: positions a view below another |
| **layout_columnSpan** | `GridLayout` attribute: makes a child span multiple columns |
| **padding** | Space inside a view's border |
| **margin** | Space outside a view's border |
| **gravity** | Aligns content inside a view |
| **layout_gravity** | Aligns the view itself inside its parent |

---

## 📝 Practice Questions — Topic 5

1. What is a ViewGroup? How is it different from a View?
2. What attribute controls direction in a `LinearLayout`? What are the two values?
3. Draw what a vertical `LinearLayout` with three `Button` children looks like on screen.
4. What does `layout_weight="1"` do when two Buttons each have this in a horizontal LinearLayout?
5. Write the `RelativeLayout` XML attributes to place a Button in the **bottom-right corner** of the screen.
6. Write the XML to position a `TextView` BELOW an `EditText` with id `@+id/nameInput` in a RelativeLayout.
7. What is FrameLayout used for? Give a real-world example of when you would use it.
8. In a GridLayout with 3 columns, write the XML attribute to make a Button span all 3 columns.
9. Why does a ScrollView's single child usually have `layout_height="wrap_content"` instead of `match_parent`?
10. `ScrollView` can only have ONE direct child. What is the common pattern to scroll multiple views?
11. What is the main advantage of ConstraintLayout over nested LinearLayouts?
12. What is the difference between `android:padding` and `android:layout_margin`?
