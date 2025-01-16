
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

or for heavy model

```sh
curl -o https://storage.googleapis.com/mediapipe-models/pose_landmarker/pose_landmarker_heavy/float16/latest/pose_landmarker_heavy.task
```

4. Edit parameters at the top of the notebook -
resolution of video, fps, model path, etc.

5. Edit model options: `THRESHOLD` and `CUTOFF`

- `THRESHOLD` [0.0-1.0] - defines how much distance a POINT has to travel to be rejected
- `CUTOFF` [0.0-1.0] - defines how large a percentage of the points in FRAME must be discarded in order to discard FRAME


6. Configure drawing tasks in the notebook (above "video export" at
the bottom of the notebook)

After running notebook it will generate `mp_data.pkl` which contains
the parsed images and will be saved to reduce processing time on next
runs.

The resulting video is saved as `output.mp4`.