# Quest Display Access Demo

This project is a modified version of [QuestDisplayAccessDemo](https://github.com/trev3d/QuestDisplayAccessDemo/tree/master), aiming to improve the functionality of display access on the Meta Quest. While developers haven't been granted camera access on Meta Quest yet, the next best alternative is display access. Using Android's `MediaProjection` API, this project copies the display image to a texture in your Unity project in "near real-time" (with several frames of latency). This Unity demo showcases that functionality, requiring no PC, embedded browser, or developer mode.

---

## ⚠️ Known Issues (Please Read)

### To Fix
- **MediaProjection Stop Callback:** The callback doesn't function correctly, causing issues when attempting to stop media projection.

### Gotchas
- **Unity Activity Setup:** The app must launch using the `UnityPlayerActivityWithMediaProjector` activity. To enable this, modify your AndroidManifest file. [More info here.](https://developer.android.com/reference/android/media/projection/MediaProjection)
- **CPU Usage:** When display capture is enabled, expect around 10% CPU usage. This demo isn't optimized!
- **Quest Software Requirements:** Ensure your Quest system software is version 68 or higher.
- **QuestLink Compatibility:** This demo only works on the headset itself. It will not work through QuestLink.
- **Recording Limitations:** You cannot record the display normally while the MediaProjector session is active. However, you can use `scrcpy` to record any prototypes or demos.
- **Virtual Elements & Camera Access:** Since this is not proper camera access, virtual elements in the scene will obscure real-world objects in the captured image. Be sure not to render anything on top of objects you wish to track!

---

## Other Info
- The captured view has ~82 degrees horizontal and vertical FOV on Quest 3.
- Capture texture resolution is 1024x1024 (on Quest 3).
- Captured frames come from the left eye buffer.
- Quest system camera settings do not affect capture resolution, framerate, or eye side.

---

## To-Do (Future Plans)
- **AprilTag VR Tracking:** While not currently active in this demo, I am working on integrating AprilTag tracking. This feature will include head pose tracking synced with the display capture. The prototype is still in progress, but head pose isn't yet correctly matched to the tag positions, causing "flickering" when moving the head. Future iterations aim to resolve these issues and provide more reliable tracking.

---

## References
- [Oculus MediaProjection Documentation](https://developer.oculus.com/documentation/native/native-media-projection/)
- [Android MediaProjection API](https://developer.android.com/media/grow/media-projection)
- [Media Samples - Screen Capture](https://github.com/android/media-samples/tree/main/ScreenCapture)
- [Original QuestDisplayAccessDemo](https://github.com/trev3d/QuestDisplayAccessDemo/tree/master)
