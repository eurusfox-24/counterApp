# Simple Counter Application (Android/Jetpack Compose)

A minimalistic Android application built using **Kotlin** and **Jetpack Compose** to demonstrate basic state management and composable UI elements.

## ✨ Features

This application provides a simple, functional counter interface:

* **Increment Button:** Increases the counter value by one.
* **Decrement Button:** Decreases the counter value by one.
* **Editable Text Field:** Allows the user to directly view and change the counter value by typing.
* **State Management:** The counter state is preserved and managed using Compose's `remember` and `mutableStateOf` functions, ensuring the UI automatically updates.

| Feature | Description |
| :--- | :--- |
| **User Input** | Buttons for increment/decrement, and a text field for direct editing. |
| **State** | Managed via Compose's state system for automatic UI recomposition. |
| **Layout** | Simple horizontal `Row` to align all controls. |

## 🛠️ Technology Stack

| Component | Technology |
| :--- | :--- |
| **Language** | Kotlin |
| **UI Toolkit** | Jetpack Compose |
| **Platform** | Android |

## ⚙️ Project Structure

The core logic is contained within the `MainActivity.kt` file.

### `MainActivity.kt`

* **`MainActivity`**: Sets up the Compose environment using `setContent` and applies the app theme.
* **`Counter()` Composable**:
    * Holds the counter state using `var count by remember { mutableStateOf("0") }`.
    * Uses a `Row` layout to arrange the buttons and the `TextField` horizontally.
    * The Decrement Button uses `Icons.Filled.Remove`.
    * The Increment Button uses `Icons.Filled.Add`.
    * The `TextField` handles user input and updates the state (converting the string back to an integer for math, and then back to a string for display).

## 🚀 Usage

### Prerequisites

* **Android Studio** (Jellyfish or newer recommended)
* A physical Android device or an Android Emulator

### Installation

1.  **Clone the Repository:**
    ```bash
    git clone [Your Repository URL]
    cd counterapp
    ```
2.  **Open in Android Studio:**
    * Open Android Studio and select "Open an existing project."
    * Navigate to the project root directory (`counterapp`) and open it.
3.  **Run the App:**
    * Select a target device/emulator.
    * Click the **Run button** (green arrow) in the toolbar.

## 👨‍💻 Key Code Snippet (State Management)

The use of `mutableStateOf` and the `by remember` delegate is central to the application. It ensures the UI automatically recomposes (updates) when the `count` variable changes, driving the entire application.

```kotlin
// The counter value, stored as a string to accommodate the TextField's requirements
var count by remember { mutableStateOf("0") }

// ... inside the Increment Button's onClick ...
onClick = {
    // Safely convert to Int, increment, and convert back to String
    count = (count.toIntOrNull()?.plus(1) ?: 0).toString()
}

// ... inside the Decrement Button's onClick ...
onClick = {
    // Safely convert to Int, decrement, and convert back to String
    count = (count.toIntOrNull()?.minus(1) ?: 0).toString()
}

// ... inside the TextField's onValueChange ...
onValueChange = { newValue ->
    // Update the state with the new input string
    count = newValue
}
