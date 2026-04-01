🚨 Emergency Sound Detection — Android Frontend
📱 Overview

The Android frontend of the Emergency Sound Detection system is developed using Java and is designed to provide a responsive and user-friendly interface. The application consists of two main screens: MainActivity, which functions as the monitoring dashboard, and AlertPopupActivity, which displays a full-screen emergency alert over the home or lock screen when a threat is detected.

🖥️ Screens

🔹 MainActivity (Dashboard)

The MainActivity serves as the primary interface for users to monitor and control the detection system. It displays real-time detection results and allows users to start or stop the background monitoring service.

The application operates in three states:

Idle, when monitoring is not active
Monitoring, where the app continuously listens for sounds
Emergency, where a flashing alert is displayed along with the detected sound and its confidence level

Users can also stop vibration alerts without interrupting the monitoring process, ensuring continuous detection.

🔹 AlertPopupActivity (Emergency Popup)

The AlertPopupActivity is triggered during emergency situations and is designed to immediately capture user attention. It appears as a full-screen popup over the home screen or lock screen and automatically wakes the device.

The popup displays a large emoji representing the detected sound, along with the sound label and confidence percentage. It also provides options to stop the vibration or dismiss the alert. A color-based flash animation is used to enhance visibility and urgency.

🎨 Sound Color Mapping

Each detected sound is associated with a specific color to enable quick visual recognition during emergencies:

Sound	Color
Siren	#FF8800
Glass Break	#FF1A1A
Baby Cry	#FFDD00
Car Horn	#FF6600
Explosion	#FF0000
Loud Noise	#FF9500
🔄 Communication Flow

The frontend communicates with the background DetectionService through broadcasts and notifications. Detection results are sent to the MainActivity to update the UI in real time. At the same time, a full-screen notification triggers the AlertPopupActivity when the app is running in the background. Both screens can send a broadcast to stop vibration without affecting the monitoring process.

🔐 Permissions

The application requires several permissions to function properly. Microphone access is needed for sound detection, while foreground service permission ensures continuous background operation. Wake lock is used to turn on the screen during alerts, and system alert window permission allows the popup to appear over other applications. On Android 14 and above, full-screen intent permission is required for displaying emergency alerts.

🎨 Theme

The application is built using Material 3 with a no-action-bar configuration to maintain a clean and modern design. The alert popup uses a fullscreen layout with a dimmed background to highlight emergency alerts effectively.

⚙️ Key Design Decisions

The system is designed to avoid duplicate vibrations by handling all vibration logic exclusively within the DetectionService. The “Stop Vibration” feature does not stop monitoring, allowing the app to continue detecting sounds. The popup uses a wake lock for up to 30 seconds to ensure visibility, and the application continues to function reliably even when running in the background.

▶️ How to Run

To run the application, install the APK on a device running Android 10 or above and grant all required permissions. Start the monitoring process from the dashboard and minimize the app if needed. When an emergency sound is detected, a full-screen popup alert will appear automatically.

✨ This version is:

Clean and easy to read
More professional (like a project submission)
Perfect for GitHub + viva + recruiters
