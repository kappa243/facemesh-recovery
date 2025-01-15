
## Usage:

1. Record or use any type of video.

2. Extract frames from the video using ffmpeg (you can increase the fps to get more frames that can be detected by the parsing process
and used for landmark recovery)

```sh
ffmpeg -i "file.mp4" -qscale:v 2 -vf fps=30 "input/frame_%04d%.jpg"
```

3. Download latest pose landmark model

```sh
curl -o https://storage.googleapis.com/mediapipe-models/pose_landmarker/pose_landmarker_full/float16/latest/pose_landmarker_full.task
```

4. Edit parameters at the top of the notebook -
resolution, fps, etc.

5. Configure drawing tasks in the notebook (above "video export" at
the bottom of the notebook)

After running notebook it will generate `mp_data.pkl` which contains
the parsed images and will be saved to reduce processing time on next
runs.

The resulting video is saved as `output.mp4`.