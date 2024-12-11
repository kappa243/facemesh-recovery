
## Usage:

1. Record or use any type of video. Face should take up most of the
frame space

2. Extract frames from the video using ffmpeg (you can increase the fps to get more frames that can be detected by the parsing process
and used for landmark recovery)

```sh
ffmpeg -i "file.mp4" -qscale:v 2 -vf fps=30 "input/frame_%04d%.jpg"
```

3. Download latest face_landmark model

```sh
curl -o face_landmarker.task https://storage.googleapis.com/mediapipe-models/face_landmarker/face_landmarker/float16/latest/face_landmarker.task
```

4. Edit parameters at the top of the notebook -
resolution, fps, etc.

5. Configure drawing tasks in the notebook (above "video export" at
the bottom of the notebook)

After running notebook it will generate `mp_data.pkl` which contains
the parsed images and will be saved to reduce processing time on next
runs.

The resulting video is saved as `output.mp4`.