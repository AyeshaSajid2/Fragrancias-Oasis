# Flutter Project

## Overview
This is a Flutter-based mobile application integrated with Firebase services, including Firebase Cloud Messaging (FCM) for push notifications.

## Prerequisites
Before installing and running the app, ensure you have the following:

- [Flutter](https://flutter.dev/docs/get-started/install) (Latest stable version)
- [Android Studio](https://developer.android.com/studio) or [VS Code](https://code.visualstudio.com/)
- Android SDK & Emulator (if running on Android)
- Xcode & CocoaPods (if running on iOS)
- A Firebase project with ownership access (provided by the client)

## Installation

1. **Unzip the code folder**
   ```sh
 
   ```

2. **Install dependencies**
   ```sh
   flutter pub get
   ```

3. **Setup Firebase**
    - Obtain the Firebase project access from the client.
    - firebase is already setup just take the firebase ownership rights.
    - Download the `google-services.json` (for Android) and `GoogleService-Info.plist` (for iOS) from Firebase Console.
    - Place `google-services.json` inside `android/app/`.
    - Place `GoogleService-Info.plist` inside `ios/Runner/`.

4. **Enable Firebase Services**
    - When you have firebase acccess below steps are not needed.
    - Enable **Firebase Cloud Messaging (FCM)** in the Firebase Console.
    - Set up Firebase Authentication if required.
    - Enable Firestore and Firebase Storage if used.

## Running the App

### For Android:
```sh
flutter run
```

### For iOS:
```sh
cd ios && pod install && cd ..
flutter run
```


### For Ios
Here are the steps for someone with macOS to run the project with Firebase Cloud Messaging (FCM):

---

### Steps to Run the Project with Firebase Cloud Messaging (FCM) on macOS

1. **Install Dependencies**
    - Open the terminal and navigate to the project’s `ios` directory.
      ```bash
      cd ios/
      ```
    - Install the required dependencies using CocoaPods:
      ```bash
      pod install
      ```

2. **Open the Project in Xcode**
    - Open the `.xcworkspace` file in Xcode:
      ```bash
      open Runner.xcworkspace
      ```

3. **Ensure Firebase Setup is Correct**
    - Ensure that the `GoogleService-Info.plist` file is added to the `ios/Runner` directory.
    - In Xcode, right-click on the project folder in the project navigator, then click **Add Files to "Runner"** and select the `GoogleService-Info.plist` file.
    - Make sure the file is included under **Build Settings > Packaging > Copy Bundle Resources**.

4. **Check `AppDelegate.swift`**
    - Ensure that your `AppDelegate.swift` has the Firebase and FCM setup.
   
5. **Update `pubspec.yaml`**
    - Ensure the dependencies are added to `pubspec.yaml` for Firebase Core and Firebase Messaging:
      ```yaml
      dependencies:
        firebase_core: ^1.0.0
        firebase_messaging: ^10.0.0
      ```
    - Run the command:
      ```bash
      flutter pub get
      ```

6. **Request Notification Permissions**
    - Update `AppDelegate.swift` to request notification permissions as shown below:
      ```swift
      UNUserNotificationCenter.current().requestAuthorization(options: [.alert, .badge, .sound]) { granted, error in
          if granted {
              DispatchQueue.main.async {
                  application.registerForRemoteNotifications()
              }
          }
      }
      ```

7. **Configure Firebase Messaging in Flutter**
    - In `main.dart`, initialize Firebase:

8. **Handle Foreground Notifications in Flutter**
    - In `main.dart`, listen for foreground notifications:

9. **Test Push Notifications**
    - Run the app on a **real iOS device** (not the simulator).
    - Make sure the device is registered for push notifications and Firebase Cloud Messaging.
    - Send a test notification from the Firebase Console to verify that the push notifications are working.

---

### Additional Notes:
- **macOS Requirements**: Ensure you are running the latest version of Xcode and Flutter with Firebase dependencies correctly set up.
- **Real Device Testing**: FCM push notifications will only work on a real iOS device. The simulator does not support receiving push notifications.

These steps should help the person with macOS to run the Flutter project with Firebase Cloud Messaging (FCM) and test push notifications.
(Ensure you run on a real device for push notifications, as FCM doesn't work on iOS simulators.)

## Firebase Cloud Messaging (FCM)
- The app is subscribed to the `all_users` topic to receive notifications.
- Notifications will display the title, message, and image (if provided).
- Ensure your device has Google Play Services enabled.

## Troubleshooting
- If you face build issues, try running:
  ```sh
  flutter clean
  flutter pub get
  ```
- For iOS build errors, run:
  ```sh
  cd ios
  pod install --repo-update
  cd ..
  ```
- If push notifications aren't working, ensure:
    - Firebase messaging is correctly configured.
    - Background notification handlers are set up.
    - The device is subscribed to the notification topic.

## Additional Configurations
- Modify `android/app/build.gradle` for Firebase dependencies.
- Modify `ios/Runner/Info.plist` for Firebase permissions.

## Contact
For firebase access, contact 'ayeshasajid391@gmail.com`.

