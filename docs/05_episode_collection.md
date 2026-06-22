# Episode Collection

This section explains the complete process for collecting color sortation demonstration episodes.

## Purpose

Episode collection is performed to record examples of the robot observing and interacting with colored blocks.

These demonstrations will later be used to train the robot for color-based sorting behavior.

## Before Recording

Check the following before starting:

- Robot is powered on
- Camera feed is visible
- Teleoperation works correctly
- Correct task is selected
- Colored block is visible
- Workspace is clear
- Recording folder is ready

## Episode Collection Procedure

Follow these steps:

1. Place the colored block in the working area.
2. Make sure the block is visible in the robot camera view.
3. Open the Data Collection UI.
4. Select the correct color sortation task.
5. Run a dry test if needed.
6. Start the recording session.
7. Control the robot through teleoperation.
8. Move the robot toward the colored block.
9. Record the camera view and robot movement.
10. Stop the recording session.
11. Save the episode in the correct color folder.
12. Review the recording.
13. Re-record if the episode quality is poor.
14. Repeat the process with different colors, sizes, and positions.

## Recording Guidelines

A good recording should include:

- Clear view of the colored block
- Stable camera feed
- Smooth robot movement
- Correct color category
- Useful demonstration behavior
- Correct file placement

## Poor Recording Examples

Re-record the episode if:

- The object is not visible
- The camera feed freezes
- Lighting is too poor
- The robot movement is not useful
- The wrong color is recorded
- The recording is incomplete
- The episode is saved in the wrong folder

## Recommended Variation

To improve dataset quality, record with:

- Different block positions
- Different object distances
- Different block sizes
- Different starting positions
- Slightly different viewing angles

## Example Recording Image

![Robot Setup](assets/robot_setup.jpg)

## Notes

Good episode quality is more important than collecting a large number of poor recordings.

A clean dataset will improve training quality and reduce problems during model evaluation.
