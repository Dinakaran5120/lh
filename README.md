Step 1 — Unzip the file
bashunzip luptup_lib.zip
This creates a folder called luptup_package/.

Step 2 — Copy files into your Flutter project
Replace ~/your_flutter_project with your actual project path:
bashcp -r luptup_package/lib/screens   ~/your_flutter_project/lib/
cp -r luptup_package/lib/navigation ~/your_flutter_project/lib/
cp -r luptup_package/lib/theme      ~/your_flutter_project/lib/
cp    luptup_package/lib/main.dart  ~/your_flutter_project/lib/main.dart

Step 3 — Open pubspec.yaml and add dependencies
bashcd ~/your_flutter_project
Open pubspec.yaml and under dependencies: add these 3 lines:
yamldependencies:
  flutter:
    sdk: flutter
  go_router: ^14.0.0
  provider: ^6.1.2
  shared_preferences: ^2.3.0

Step 4 — Install the packages
bashflutter pub get

Step 5 — Create the assets folders
bashmkdir -p assets/images
mkdir -p assets/icons
Then in pubspec.yaml under the flutter: section add:
yamlflutter:
  uses-material-design: true
  assets:
    - assets/images/
    - assets/icons/

Step 6 — Run the app
bashflutter run

Quick one-liner (Steps 1–4 combined)
If your Flutter project is at ~/luptup:
bashunzip luptup_lib.zip && \
cp -r luptup_package/lib/screens ~/luptup/lib/ && \
cp -r luptup_package/lib/navigation ~/luptup/lib/ && \
cp -r luptup_package/lib/theme ~/luptup/lib/ && \
cp luptup_package/lib/main.dart ~/luptup/lib/main.dart && \
cd ~/luptup && \
flutter pub get && \
flutter run

What to expect on first run
The app will open on SplashLoginScreen. Since _authNotifier.value = false by default, all protected routes redirect back to splash. To test the home screen temporarily, open app_router.dart and change one line:
dart// Change this:
final _authNotifier = ValueNotifier<bool>(false);

// To this (temporary, for UI testing):
final _authNotifier = ValueNotifier<bool>(true);
That will skip auth and land directly on DiscoverScreen with the full bottom navigation working.Sonnet 4.6



C:\Users\dinak\luptup>flutter run
Launching lib\main.dart on sdk gphone64 x86 64 in debug mode...
Running Gradle task 'assembleDebug'...                            143.7s
√ Built build\app\outputs\flutter-apk\app-debug.apk
Installing build\app\outputs\flutter-apk\app-debug.apk...           9.1s
D/FlutterJNI(14591): Beginning load of flutter...
D/FlutterJNI(14591): flutter (null) was loaded normally!
I/flutter (14591): [IMPORTANT:flutter/shell/platform/android/android_context_gl_impeller.cc(104)] Using the Impeller rendering backend (OpenGLES).
D/FlutterRenderer(14591): Width is zero. 0,0
D/FlutterRenderer(14591): Width is zero. 0,0
D/FlutterJNI(14591): Sending viewport metrics to the engine.
I/Gralloc4(14591): mapper 4.x is not supported
W/OpenGLRenderer(14591): Failed to choose config with EGL_SWAP_BEHAVIOR_PRESERVED, retrying without...
W/OpenGLRenderer(14591): Failed to initialize 101010-2 format, error = EGL_SUCCESS
E/OpenGLRenderer(14591): Unable to match the desired swap behavior.
Syncing files to device sdk gphone64 x86 64...                   1,265ms

Flutter run key commands.
r Hot reload.
R Hot restart.
h List all available interactive commands.
d Detach (terminate "flutter run" but leave application running).
c Clear the screen
q Quit (terminate the application on the device).

A Dart VM Service on sdk gphone64 x86 64 is available at: http://127.0.0.1:52732/AucWMlfl_Vw=/
The Flutter DevTools debugger and profiler on sdk gphone64 x86 64 is available at:
http://127.0.0.1:52732/AucWMlfl_Vw=/devtools/?uri=ws://127.0.0.1:52732/AucWMlfl_Vw=/ws
I/Choreographer(14591): Skipped 267 frames!  The application may be doing too much work on its main thread.
D/FlutterJNI(14591): Sending viewport metrics to the engine.
D/ProfileInstaller(14591): Installing profile for com.example.luptup
D/EGL_emulation(14591): app_time_stats: avg=5371.54ms min=128.10ms max=25843.52ms count=5
D/EGL_emulation(14591): app_time_stats: avg=429.78ms min=6.32ms max=7210.74ms count=18
D/EGL_emulation(14591): app_time_stats: avg=929.48ms min=22.57ms max=14250.19ms count=16
