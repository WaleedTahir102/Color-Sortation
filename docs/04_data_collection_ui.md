# Data Collection UI

This section explains how the Data Collection UI is used for the color sortation task.

The official Trossen Data Collection UI provides features for robot configuration, task configuration, live camera monitoring, recording controls, progress tracking, and dataset saving.

## Pre-Installation Setup

Before installing or using the Trossen AI Data Collection UI, prepare the system environment.

### 1. Install Miniconda

Install Miniconda to manage the Python environment for the UI application.

### 2. Create Virtual Environment

Create a clean Python environment for the application:

```bash
conda create -n trossen_ai_data_collection_ui_env python=3.10 -y
conda activate trossen_ai_data_collection_ui_env
```

### 3. Verify Python Version

Check that Python 3.10 is active:

```bash
python --version
```

Expected output:

```text
Python 3.10.x
```

---

## Installation of UI Application

After preparing the environment, install the required application.

### 1. Install Linux Build Dependencies

```bash
sudo apt-get install -y \
build-essential \
cmake \
libavcodec-dev \
libavdevice-dev \
libavfilter-dev \
libavformat-dev \
libavutil-dev \
libswresample-dev \
libswscale-dev \
pkg-config \
python3-dev
```

### 2. Install the Data Collection UI

```bash
pip install trossen_ai_data_collection_ui
```

### 3. Run Post-Installation Setup

```bash
trossen_ai_data_collection_ui_post_install
```

The post-installation script prepares required dependencies, fixes common video/camera library issues, and creates a desktop launcher for the UI.

---

## Updating the UI Application

Updating is recommended when the UI does not work correctly, cameras are not detected properly, or the latest fixes are required.

To update:

```bash
conda activate trossen_ai_data_collection_ui_env
pip install trossen_ai_data_collection_ui --upgrade
trossen_ai_data_collection_ui_post_install
```

Do not manually edit the internal UI dependency folder because it is managed automatically by the post-installation script.

---

## Launching the Application

The UI can be launched in two ways.

### Option 1: Desktop Launcher

After installation, use the desktop shortcut:

```text
Trossen AI Data Collection UI
```

If the shortcut does not open, right-click it and select:

```text
Allow Launching
```

### Option 2: Command Line

Launch the UI from terminal:

```bash
conda activate trossen_ai_data_collection_ui_env
trossen_ai_data_collection_ui
```

---

## Configuring the Robot

Robot configuration is used to define the robot model, camera settings, camera serial numbers or indexes, IP addresses, and movement-related parameters.

To configure the robot:

1. Launch the Trossen AI Data Collection UI.
2. Click `Edit` from the top menu.
3. Select `Robot Configuration`.
4. Update the required YAML fields.
5. Save the configuration.
6. Restart or reload the UI if needed.

The UI supports different robot profiles such as:

```yaml
trossen_ai_stationary
trossen_ai_mobile
trossen_ai_solo
```

For this project, use the robot profile that matches the actual setup. If the robot is a mobile setup, use the mobile robot configuration. If the UI is configured as a stationary setup, keep the stationary profile and only update the required camera/IP values.

### Important Robot Configuration Fields

| Field                         | Purpose                                                   |
| ----------------------------- | --------------------------------------------------------- |
| `max_relative_target`         | Safety limit for robot motion                             |
| `min_time_to_move_multiplier` | Controls movement smoothness and speed                    |
| `camera_interface`            | Defines camera backend, such as `opencv`                  |
| `leader_arms`                 | IP/model settings for leader arms, if used                |
| `follower_arms`               | IP/model settings for follower arms, if used              |
| `cameras`                     | Camera names, serial numbers/indexes, resolution, and FPS |

### Example Robot Configuration

```yaml
trossen_ai_stationary:
  max_relative_target: null
  min_time_to_move_multiplier: 3.0
  camera_interface: "opencv"

  leader_arms:
    right:
      ip: "192.168.1.3"
      model: "V0_LEADER"
    left:
      ip: "192.168.1.2"
      model: "V0_LEADER"

  follower_arms:
    right:
      ip: "192.168.1.5"
      model: "V0_FOLLOWER"
    left:
      ip: "192.168.1.4"
      model: "V0_FOLLOWER"

  cameras:
    cam_high:
      serial_number: 0
      width: 640
      height: 480
      fps: 30

    cam_low:
      serial_number: 1
      width: 640
      height: 480
      fps: 30
```

### Notes for Camera Configuration

* If `camera_interface` is set to `opencv`, use the camera index such as `0`, `1`, or `2`.
* If using Intel RealSense cameras, use the actual camera serial number.
* Do not change camera names unless the UI configuration requires it.
* Make sure the selected resolution and FPS are supported by the camera.
* If the camera is not showing in the UI, check the camera index/serial number first.

### Notes for Motion Configuration

* A smaller `min_time_to_move_multiplier` can make movement faster but may cause jerky motion.
* A larger value makes movement smoother but may increase delay.
* Use a safe value first, then adjust only after testing with a dry run.

## Configuring the Task

Task configuration defines how the color sortation data collection session will run.

To configure the task:

1. Launch the Data Collection UI.
2. Click `Edit`.
3. Select `Task Configuration`.
4. Add or edit the color sortation task.
5. Save the configuration.
6. Select the task from the UI dropdown before recording.

Recommended task configuration fields:

| Field              | Purpose                                 |
| ------------------ | --------------------------------------- |
| `task_name`        | Unique name of the color sortation task |
| `robot_model`      | Robot configuration used for the task   |
| `task_description` | Short explanation of the task           |
| `episode_length_s` | Duration of each recording              |
| `warmup_time_s`    | Time before recording starts            |
| `reset_time_s`     | Time between recordings                 |
| `hf_user`          | Hugging Face username                   |
| `fps`              | Recording frame rate                    |
| `push_to_hub`      | Upload dataset to Hugging Face          |
| `display_fps`      | Camera preview refresh rate             |
| `operators`        | Names/emails of operators               |

Example task description:

```text
Color sortation task using the Trossen Mobile AI Robot. The robot observes red, blue, and green colored blocks through its camera while demonstration episodes are collected using teleoperation. The recorded episodes are used for robot training and testing.
```

Suggested color sortation task example:

```yaml
- task_name: "color_sortation"
  robot_model: "trossen_ai_mobile"
  task_description: "Color sortation task using red, blue, and green colored blocks."
  episode_length_s: 10
  warmup_time_s: 5
  reset_time_s: 5
  hf_user: "your_huggingface_username"
  fps: 30
  push_to_hub: false
  play_sounds: true
  disable_active_ui_updates: false
  save_interval: 1
  display_fps: 1
  operators:
    - name: "operator_name"
      email: "operator_email@example.com"
```

---

## Important Notes

* Use `Dry Run` before actual recording.
* Confirm the camera view before starting an episode.
* If camera preview causes lag, reduce `display_fps`.
* If the robot movement is jerky, adjust movement-related configuration carefully.
* Use `Re-record Last Episode` if the object is not visible or the robot movement is incorrect.
* Check that each episode is saved in the correct color category.


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
