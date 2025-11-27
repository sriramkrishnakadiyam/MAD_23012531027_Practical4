Android Alarm Application with Service and BroadcastReceiver 

AIM
To build an Android application that lets the user set a one-time alarm, which will play a sound at the selected time using a Service. The user can also cancel the alarm, stopping the sound and preventing it from ringing again.

Features
1. Set Alarm
A TimePickerDialog opens when the user taps the Create button, allowing them to choose a time.

2. Show Alarm Time
After the alarm is set, the selected time appears on a card.
3. Alarm Sound
When the selected time arrives, a sound plays automatically.
4. Cancel Alarm
The user can cancel the alarm.
If the alarm sound is currently playing, it stops immediately.
5. Exact Alarm Support
The app uses the permission:
SCHEDULE_EXACT_ALARM
to ensure the alarm triggers accurately on modern Android versions.
6. Material Design UI
The layout uses MaterialCardView, MaterialButton, and ConstraintLayout for a clean interface.

App Screenshots
![image alt](https://github.com/sriramkrishnakadiyam/MAD_23012531027_Practical4/blob/6e6218a9ee30ca6cff752a5277dec8a0456f327f/Screenshot%202025-11-27%20142136.png)

Core Concepts Demonstrated
1. Service
A background component (AlarmService)
Plays the alarm sound with MediaPlayer, even if the app is not open
2. BroadcastReceiver
AlarmBroadcastReceiver receives the alarm trigger from AlarmManager
Starts the Service to play the alarm sound
3. AlarmManager
Schedules and cancels alarms
Uses setExact() to fire at the exact chosen time
4. PendingIntent
Wraps an intent so AlarmManager can run it later
Grants permission to trigger the BroadcastReceiver
5. TimePickerDialog
Lets users choose the alarm time easily
6. Calendar & SimpleDateFormat
Used to handle time values
Formats the displayed alarm time

7. MediaPlayer
Plays alarm audio stored in res/raw/alarm.mp3
8. Permissions
Declares SCHEDULE_EXACT_ALARM in the manifest
Redirects user to system settings if permission is not granted
9. UI Visibility Control
Shows or hides the alarm card using:
View.VISIBLE

View.GONE

Project Structure
MainActivity.kt
Handles setting and canceling alarms
Shows TimePickerDialog
Manages UI and AlarmManager interaction
AlarmService.kt
A Service that plays and stops the alarm sound using MediaPlayer
AlarmBroadcastReceiver.kt
Gets triggered by AlarmManager
Starts the AlarmService
activity_main.xml
Layout created with ConstraintLayout and Material Components
AndroidManifest.xml
Declares:
Activities

BroadcastReceiver

Service

Includes permissions
