# RGB-D Dataset for Emotion-based Place Recognition

The camera configuration / preferences, the process to obtain these and the recording steps are described below in each separate section. The code and readme maintenance will be made according to next Master's phases.

# Camera configuration values

The camera used to capture the frames will be the Intel RealSense R200, which was designed to focus on medium distances and can capture RGB-D (color and depth data) with frame detection up to 60 fps. As this experiment has to worry about disk space limitations and the number of frames per second doesn't need to be too big in order to accomplish the task, the default value considered will be 30 fps.