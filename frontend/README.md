🚨 Emergency Sound Detection — Android Frontend
📱 Overview

Android frontend built using Java with two main screens:

MainActivity → Monitoring dashboard
AlertPopupActivity → Full-screen emergency alert (works over lock/home screen)
🖥️ Screens
🔹 MainActivity (Dashboard)

Displays real-time detection and allows users to control monitoring.

✨ Key Features
Start/Stop background detection
View detected sound + confidence
Emergency UI with flashing alert
Stop vibration (without stopping monitoring)
📊 States
Idle → Not running
Monitoring → 🎤 Active listening
Emergency → Flash + alert display
🔹 AlertPopupActivity (Emergency Popup)
Appears over home screen & lock screen
Automatically wakes the device
Displays:
Emoji + sound label
Confidence %
Stop vibration / Dismiss buttons
Includes color flash animation
🎨 Sound Color Mapping
Sound	Color
Siren	#FF8800
Glass Break	#FF1A1A
Baby Cry	#FFDD00
Car Horn	#FF6600
Explosion	#FF0000
Loud Noise	#FF9500
🔄 Communication Flow
DetectionService
   ├── Broadcast → MainActivity (UI update)
   ├── FullScreen Notification → AlertPopupActivity
   └── Stop Vibration Broadcast ← UI
🔐 Permissions
RECORD_AUDIO → Microphone access
FOREGROUND_SERVICE → Background detection
WAKE_LOCK → Wake screen on alert
SYSTEM_ALERT_WINDOW → Display over apps
USE_FULL_SCREEN_INTENT → Required for Android 14+
🎨 Theme
Based on Material 3 (No Action Bar)
Popup is fullscreen with dimmed background
⚙️ Key Design Decisions
✅ Vibration handled only by DetectionService (prevents duplication)
✅ “Stop Vibration” does not stop monitoring
✅ Popup uses wake lock (max 30 seconds)
✅ Works even when app is backgrounded
▶️ How to Run
Install APK (Android 10+)
Grant required permissions
Tap Start Monitoring
Minimize app (home button)
Play emergency sound → Popup appears 🚨
