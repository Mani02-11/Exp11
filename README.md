# 📱 Experiment 11 – Display a Map Using Google Maps API

## Develop an Android Application to Display a Map Using Google Maps API

---

## 👨‍💻 Author

**Name:** Manikandan P  
**USN:** 25MCAR0186  
**Subject:** Mobile Application Development Lab

---

## 📖 Experiment Description

This experiment demonstrates integrating the **Google Maps SDK for Android** with Kotlin and XML to display an interactive map, request runtime location permissions, and show the user's real-time position.

The application embeds Google Maps using `SupportMapFragment` and configures the required API Key in `AndroidManifest.xml`. It requests `ACCESS_FINE_LOCATION` and `ACCESS_COARSE_LOCATION` permissions at runtime. 

Upon granting permission, the application utilizes `FusedLocationProviderClient` to retrieve the device's real-time GPS coordinates, enables the "My Location" blue dot layer on the map, and smoothly animates the camera to center on the user's location.


### Scenario

The application simulates a **Live Location Map and Student ID Display**.

```text
              Google Maps Location App
                         ↓
                 Display Main Screen
                         ↓
            Request Location Permission
                         ↓
               Permission Granted?
                   ↙           ↘
                 Yes            No
                  ↓              ↓
           Enable Live      Show Permission
            Location            Message
                  ↓
          Fetch Current GPS
              Coordinates
                  ↓
          Center Google Map &
          Show Location Dot
                  ↓
           Display Student Details
             (Name & USN Card)
```

---

## 🧠 Concept / Technology Used

### Google Maps SDK & Play Services Location

The Google Maps SDK for Android provides map rendering capabilities, interactive camera controls, and custom overlays. Play Services Location API delivers energy-efficient, accurate device position tracking.

This application uses the following concepts:

* **Google Maps SDK** – Embeds interactive vector maps using `SupportMapFragment` and `GoogleMap`.
* **OnMapReadyCallback** – Interface triggered when the Google Map instance is fully loaded and ready.
* **FusedLocationProviderClient** – Fetches the device's current/last known location accurately.
* **Runtime Permissions** – Dynamically requests `ACCESS_FINE_LOCATION` and `ACCESS_COARSE_LOCATION` at runtime using `registerForActivityResult`.
* **API Key Configuration** – Configures the Google Maps API Key securely inside `AndroidManifest.xml` via `<meta-data>`.
* **Camera Animations** – Smoothly animates camera zoom to the user's GPS coordinates using `CameraUpdateFactory`.
* **Material 3 Design** – Uses `MaterialCardView` and `ConstraintLayout` to display student information cleanly alongside the map view.
* **Kotlin** – Handles map callbacks, location services, and runtime permissions.
* **XML** – Defines the user interface layout.
* **Android Studio** – Used for application development, execution, and testing.

---

# 📂 Project Structure

```text
app/
│
├── manifests/
│   └── AndroidManifest.xml
│
├── java/
│   └── com/
│       └── project/
│           └── exp11/
│               └── MainActivity.kt
│
├── res/
│   ├── layout/
│   │   └── activity_main.xml
│   │
│   └── values/
│       ├── colors.xml
│       ├── strings.xml
│       └── themes.xml
│
└── Gradle Scripts
    ├── build.gradle.kts (Module :app)
    ├── build.gradle.kts (Project)
    └── libs.versions.toml
```

---

# 🎨 User Interface

The application contains the following interface elements:

* Interactive Google Map occupying 90% of screen height
* Dynamic zoom controls (`isZoomControlsEnabled = true`)
* My Location blue indicator and location re-centering button
* Runtime location permission prompt dialog
* Permission-denied Toast notification
* Rounded Material Card at the bottom (10% screen height)
* Student details display (Name: Manikandan P, USN: 25MCAR0186)

---

# 🔑 Permissions Used

The application requires the following permissions in `AndroidManifest.xml`:

```xml
<uses-permission android:name="android.permission.INTERNET" />
<uses-permission android:name="android.permission.ACCESS_NETWORK_STATE" />
<uses-permission android:name="android.permission.ACCESS_FINE_LOCATION" />
<uses-permission android:name="android.permission.ACCESS_COARSE_LOCATION" />
```

The location permissions are requested dynamically at runtime before accessing GPS location data on supported Android versions.

---

# 🧪 Test Cases

## Test Case 1 – Application Launch and Location Permission Request

### Objective

To verify that the application launches successfully, renders the map container, and prompts for runtime location permissions.

### Input

1. Launch the Experiment 11 application.
2. Observe the runtime location permission prompt dialog.
3. Tap **While using the app** or **Only this time** to grant permission.

### Expected Result

The application should launch smoothly and display a system dialog requesting location permissions.

### Actual Result

The application launches, initializes the Google Map fragment, and prompts for location permissions as expected.

### Status

✅ **Passed**

### Screenshot – Location Permission Request

<img width="400" height="660" alt="1000180755" src="https://github.com/user-attachments/assets/f4b32ca9-083a-4652-8d1e-0939721f0740" />


---

## 🧪 Test Case 2 – Display User's Live Location on Google Map

### Objective

To verify that granting permission enables the "My Location" layer and centers the map camera on the user's real-time GPS location.

### Input

1. Grant location permission when prompted.
2. Wait for `FusedLocationProviderClient` to retrieve current GPS coordinates.

### Expected Result

The map should display the blue "My Location" dot, show the My Location re-centering button, and smoothly animate the camera to the user's location with a zoom level of 15.

### Actual Result

The camera animates directly to the user's location and displays the blue location marker on the interactive Google Map.

### Status

✅ **Passed**

### Screenshot – User Location on Map

<img width="400" height="660" alt="1000180756" src="https://github.com/user-attachments/assets/be5a7814-a0b3-4151-b444-6c1cb457dbdd" />


---

## 🧪 Test Case 3 – Display Student Details Card

### Objective

To verify that the student details card correctly displays the Name and USN at the bottom of the screen.

### Input

1. Open the application.
2. View the bottom card section below the map container.

### Expected Result

The bottom Material Card should clearly display `Name: Manikandan P` and `USN: 25MCAR0186`.

### Actual Result

The student details card displays the student Name and USN cleanly at the bottom.

### Status

✅ **Passed**

### Screenshot – Student Details Display

<img width="400" height="660" alt="1000180757" src="https://github.com/user-attachments/assets/ea3e7bb3-916f-41fa-9f53-4bea527333c8" />
