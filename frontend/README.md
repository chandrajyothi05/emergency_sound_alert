**Emergency Sound Detection — Android Frontend**
 Overview

Android frontend built using Java with two main screens:

MainActivity → Monitoring dashboard
AlertPopupActivity → Full-screen emergency alert (over lock/home screen)
 Screens
 MainActivity (Dashboard)

Displays real-time detection and controls monitoring.

Key Features:

Start/Stop background detection
View detected sound + confidence
Emergency UI with flashing alert
Stop vibration (without stopping monitoring)

States:

Idle → Not running
Monitoring → 🎤 Active listening
Emergency → Flash + alert display
 AlertPopupActivity (Emergency Popup)
Appears over home screen & lock screen
Wakes device automatically
Shows:
Emoji + sound label
Confidence %
Stop vibration / Dismiss buttons
Includes color flash animation
 Sound Color Mapping
Sound	Color
Siren	#FF8800
Glass Break	#FF1A1A
Baby Cry	#FFDD00
Car Horn	#FF6600
Explosion	#FF0000
Loud Noise	#FF9500
 Communication Flow
DetectionService
   ├── Broadcast → MainActivity (update UI)
   ├── FullScreen Notification → AlertPopupActivity
   └── Stop Vibration Broadcast ← UI
 Permissions
RECORD_AUDIO → Microphone access
FOREGROUND_SERVICE → Background detection
WAKE_LOCK → Wake screen on alert
SYSTEM_ALERT_WINDOW → Show over apps
USE_FULL_SCREEN_INTENT → Android 14+ popup
 Theme
Uses Material 3 (No Action Bar)
Popup is fullscreen, dimmed background
 Key Decisions
 Vibration handled only by DetectionService (no duplicates)
 “Stop Vibration” ≠ Stop monitoring
 Popup uses wake lock (max 30 sec)
 Works even when app is backgrounded
 How to Run
Install APK (Android 10+)
Grant required permissions
Tap Start Monitoring
Minimize app (home button)
Play emergency sound → popup appears
