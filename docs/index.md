# Color Sortation Documentation

Welcome to the color sortation documentation for the Trossen Mobile AI Robot.

This documentation explains the complete workflow for collecting color-based demonstration episodes, organizing the dataset, storing it on Hugging Face, and preparing the data for robot training.

## Documentation Purpose

The purpose of this documentation is to help new team members understand and reproduce the complete color sortation workflow.

It explains:

- What the project is about
- What hardware and software are required
- How the robot setup is prepared
- How the Data Collection UI is used
- How episodes are recorded
- How the dataset is organized
- How the data is stored on Hugging Face
- How the collected data will be used for training
- What issues may occur and how to solve them

## Overall Workflow

![Workflow](assets/workflow.png)

```text
Colored Blocks
      ↓
Robot Camera
      ↓
Teleoperation
      ↓
Episode Recording
      ↓
Dataset Organization
      ↓
Hugging Face Storage
      ↓
Model Training
      ↓
Testing and Color Sortation
```

## How to Read This Documentation

Read the pages in order:

| Step | Page                 | Purpose                               |
| ---- | -------------------- | ------------------------------------- |
| 1    | Overview             | Understand the project goal           |
| 2    | System Requirements  | Check hardware and software           |
| 3    | Setup                | Prepare robot, camera, and workspace  |
| 4    | Data Collection UI   | Understand the UI controls            |
| 5    | Episode Collection   | Record color sortation demonstrations |
| 6    | Dataset Organization | Arrange recorded data properly        |
| 7    | Hugging Face Storage | Store and share the dataset           |
| 8    | Training Preparation | Prepare data for model training       |
| 9    | Troubleshooting      | Solve common issues                   |
| 10   | Changelog            | Track documentation updates           |


## Current Status

- Robot setup completed
- Camera configuration tested
- Teleoperation-based episode collection performed
- Dataset organized by color category
- Dataset stored on Hugging Face
- Dataset prepared for future training and testing
