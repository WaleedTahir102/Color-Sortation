# Troubleshooting

This section documents common issues faced during setup and data collection.

## Camera Not Showing in Data Collection UI

### Problem

The camera feed may appear in one environment but not in the Data Collection UI.

### Possible Causes

- Incorrect camera serial number
- Wrong camera index
- IP address mismatch
- Camera configuration issue
- Camera stream not started
- Software not detecting the camera source

### Solution

1. Check the camera serial number or camera index.
2. Verify the robot IP address.
3. Restart the camera stream.
4. Restart the Data Collection UI.
5. Check robot configuration.
6. Run a dry test before recording.

## Camera Blind Spots

### Problem

Some positions may not be visible in the camera view.

### Solution

- Place objects inside the camera field of view.
- Test object position before recording.
- Avoid placing blocks too close or too far.
- Use the camera view to confirm visibility.

## Lighting Problems

### Problem

Poor lighting can make color recognition difficult.

### Solution

- Use consistent lighting.
- Avoid shadows.
- Avoid reflections.
- Keep the background simple.
- Check the camera feed before recording.

## Small Blocks Not Clear

### Problem

Smaller blocks may be difficult to see.

### Solution

- Place the block where the camera can see it clearly.
- Avoid background clutter.
- Use better lighting.
- Check visibility before starting the recording.

## Robot Movement Not Smooth

### Problem

Robot movement may be jerky or inconsistent.

### Solution

- Use slower and smoother teleoperation commands.
- Avoid sudden movements.
- Practice with dry run first.
- Re-record poor episodes.

## Dataset Saved in Wrong Folder

### Problem

An episode may be saved in the wrong color folder.

### Solution

- Review files after recording.
- Move the file to the correct folder.
- Use clear naming.
- Check folders before uploading.

## Poor Recording Quality

### Problem

Some episodes may not be useful for training.

### Possible Reasons

- Object not visible
- Wrong color object used
- Camera feed unclear
- Robot movement not useful
- Recording incomplete
- Lighting poor

### Solution

- Remove poor recordings.
- Re-record the episode.
- Keep recording conditions consistent.
- Review data before training.

## Useful Troubleshooting Images

Add these images if available:

```text
docs/assets/camera_issue.png
docs/assets/camera_fixed.png
