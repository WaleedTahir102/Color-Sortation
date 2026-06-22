# Data Collection UI

This section explains how the Data Collection UI is used for the color sortation task.

The official Trossen Data Collection UI provides features for robot configuration, task configuration, live camera monitoring, recording controls, progress tracking, and dataset saving.

## UI Purpose

The Data Collection UI is used to:

- Select the color sortation task
- Monitor camera feeds
- Start and stop recording sessions
- Track episode progress
- Re-record poor-quality episodes if required
- Save recorded demonstrations
- Manage robot and task configuration

## Launching the UI

The UI can be launched using the installed application shortcut or through the terminal, depending on the system setup.

Before launching, make sure:

- Robot is powered on
- Cameras are connected
- Teleoperation is working
- Correct robot configuration is available
- Correct task configuration is available

## Main UI Sections

The UI can be understood in the following parts:

| UI Section | Purpose |
|---|---|
| Menu bar | Access robot and task configuration |
| Camera view | Display live camera feeds |
| Task management panel | Select task and session settings |
| Progress tracking | Show recording progress |
| Log terminal | Show system messages and errors |
| Button controls | Start, stop, reset, and dry run controls |

## Menu Bar

The menu bar provides access to important settings.

Common options include:

- Robot Configuration
- Task Configuration
- Calibration options
- Quit option

## Robot Configuration

Robot configuration is used to set robot-specific parameters.

This may include:

- Camera names
- Camera serial numbers
- Camera resolution
- Camera FPS
- Robot IP addresses
- Robot model
- Motion parameters

Use this section when:

- Camera is not detected
- Robot IP address is changed
- Camera serial number is incorrect
- Robot configuration needs to be updated

## Task Configuration

Task configuration defines the data collection task.

For color sortation, the task configuration should include:

- Task name
- Task description
- Robot model
- Episode duration
- Warmup time
- Reset time
- Recording FPS
- Display FPS
- Hugging Face user
- Dataset upload option
- Operator information

## Suggested Task Description

Use this task description:

```text
Color sortation task using the Trossen Mobile AI Robot. The robot observes red, blue, and green colored blocks through its camera while demonstration episodes are collected using teleoperation. The recorded episodes are used for robot training and testing.
```

## Camera View Section

The camera view is used to check whether the colored block is visible before and during recording.

Before recording, verify:

- Block is visible
- Camera feed is stable
- Lighting is acceptable
- Object is not too close or too far
- No important part of the scene is hidden


## Button Controls

Start Recording Session

Use this button to begin collecting demonstration episodes.

Before pressing it:

- Select the correct task
- Check camera view
- Confirm robot movement
- Place the colored block correctly


## End Recording Session

Use this button to safely stop the recording session.

After stopping:

- Check whether the episode was saved
- Confirm that the system returned to idle state


## Re-record Last Episode

Use this option if the most recent episode is not useful.

Re-record if:

- Object was not visible
- Robot movement was incorrect
- Camera view was unclear
- The wrong color object was used
- Recording was interrupted


## Dry Run

Use dry run before formal recording.

Dry run helps to:

- Test camera view
- Test robot movement
- Check workspace
- Practice the task
- Avoid saving bad data


## Recommended UI Screenshot

docs/assets/teleoperation_interface.png


## Good UI Practice

Before every recording session:

- Run a dry test.
- Check the camera feed.
- Confirm the correct task is selected.
- Check that the robot moves smoothly.
- Keep the colored block in the camera view.
- Use re-record if the episode is poor quality.
