# RGB-D Dataset for Emotion-based Place Recognition

The camera configuration / preferences, the process to obtain these and the recording steps are described below in each separate section. The code and readme maintenance will be made according to next Master's phases.

# Camera configuration values

The camera used to capture the frames will be the `Intel RealSense R200`, which was designed to focus on medium distances and can capture RGB-D (color and depth data) with frame detection up to 60 fps. As this experiment has to worry about disk space limitations and the number of frames per second doesn't need to be too big in order to accomplish the task, the default value considered will be `30 fps`.

Intel RealSense R200 has support for recording of `rgb, depth and infrared` frames. In this project, all types will be used with the default resolution of `640x480`. In this way, deep learning techniques could be useful in order to analyse data and provide the classification using transfer learning neural networks that require a larger image size.

# Camera preferences process

Many configuration options are described into Intel RealSense SDK Documentation to work with R200 module on different scenarios. The open-source tool provided by Intel development kit called `cpp-config-ui` was used to obtain the best record preferences through a nice UI interface that allows real-time frame comparison.

The camera options below were choosen differing from default values and can be used for both C++/Python recording:
  - `rs_option.RS_OPTION_R200_LR_AUTO_EXPOSURE_ENABLED`: 1
  - `rs_option.RS_OPTION_R200_EMITTER_ENABLED`: 1
  - `rs_option.RS_OPTION_R200_LR_GAIN`: 2

In case of using Python it was also important to set these values below:
  - `depth_control_preset`: 5 
  - `ivcam_preset` = 8

# Record steps

The dataset will contain frame images acquired by a Intel Realsense R200 with approximately a height of `1 meter` (this value was chosen based on previous papers and the goal of avoid possible occlusions. 
In order to obtain data from general scenarios, it will be different indoor place categories:
  - `commercial`: Public indoor places such as supermarket and drugstore
  - `home`: Rooms such as living room and dinner room
  - `workplace`: Indoor rooms such as office room and meeting room

As seen above, the focus on data collection will be `indoor places` in order to keep this project based on the scenario of a robot entering in an unknown place and trying to recognize the emotional state to perform determined action.

Each category will have `25 different sample` data collected to allow the analysis of different persons and place characteristics. For example, the category “commercial” will be obtained inside two different places (supermarket / drugstore) in different times in order to get crowded / quiet moments. Moreover, the time record chosen was 8 seconds based on an appropriate period to recognize surrounding features and person emotions.

At this first moment, the emotion labels analysed for the indoor places will be based on the cross-tab below:

| Surrounding  | Emotion | Label | 
| ------------- | ------------- | ------------- |
| Quiet  | Happy  | 0 |
| Quiet  | Neutral  | 1 |
| Turbulent  | Happy  | 2 |
| Turbulent  | Neutral  | 3 |

The representation of each label in the dataset will be balanced and all the labels will be included for each place category sample. In summary, the number of samples will be `300 records` based on:

- Number of samples = 3 place categories * 25 recordings * 4 labels