# Overview

## Project Goal

The goal of this project is to prepare a structured dataset for training the Trossen Mobile AI Robot to recognize and sort colored blocks.

The task focuses on red, blue, and green colored blocks. The robot observes these objects using its camera and is manually controlled through teleoperation while demonstration episodes are recorded.

## Why Color Sortation Is Important

Color sortation is a useful robotics task because it combines:

- Robot perception
- Camera-based observation
- Teleoperation
- Demonstration recording
- Dataset organization
- Robot learning

Instead of using only fixed rules, the robot can learn from recorded demonstrations. This makes the system more flexible when objects appear in different positions, sizes, or viewing conditions.

## Main Objective

The main objective is to collect useful demonstration episodes and prepare them for training.

The collected episodes will help the robot learn:

- How colored blocks appear in the camera view
- How objects vary in size and position
- How the robot should move during the task
- How color-based sorting behavior can be learned from demonstrations

## Project Output

The final output of this work is an organized color sortation dataset that can be used for future training and testing.

## System Workflow

![Workflow](assets/workflow.png)

## Main Components

| Component | Purpose |
|---|---|
| Colored blocks | Objects used for the color sortation task |
| Robot camera | Captures visual input |
| Teleoperation | Allows manual control of the robot |
| Episode recording | Saves demonstration data |
| Dataset organization | Keeps data clean and usable |
| Hugging Face | Stores and shares the dataset |
| Training process | Uses episodes to train the robot |
