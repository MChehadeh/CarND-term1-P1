# Self-Driving Car NanoDegree - Term1 - Project1: Lane lines detection
In this project, we try to detect lane lines from recorded images/videos. **IPython** Notebook is used for running the python environment. The detection algorithm relies on *Canny edge detector* and *Hough transforn* algorithms.
***
## Software Requirement
* Python 2.7 (or higher)
* opencv
* matplotlib
* numpy
* moviepy
* IPython
## Code usage
Clone this repository or download it as a .zip file. Run "P1.ipynb" using `jupyter notebook` command.
## Lane detection pipeline
The pipeline consists of six steps (in sequence):
| Step                | Description                                                                                            | Place in code |
|---------------------|--------------------------------------------------------------------------------------------------------|---------------|
| Graying             | Converts the color image to gray                                                                       | Main          |
| Filteration         | A Gaussian filter is applied to the image                                                              | Main          |
| Edge detection      | Canny edge detector is used to find edges in the image                                                 | Main          |
| Region masking      | Edges that are outside the area of interest (i.e. the road) are masked out                             | Main          |
| Line detection      | Hough Transformation is used to select edges that represent *lines* and neglect the others             | Main          |
| Line classification | A simple line classifier based on line slopes is used to classify lanes to left lanes and right lanes  | `draw lines`  |
## Results
The results are in the repository:
* [Video-1] solidYellowLeft-Result.mp4
* [Video-2] solidWhiteRight-Result.mp4
## Known Issues
The lane line flickers sometime. This is because some other lines got detected and misclassified. Improvement is needed in **Line classification** step.
## Robustness vs Generality
The added angle limit check prevents false-positive detection of lines for the case of straight lane lines. On the other hand, this will make it impossible for the lane detector to find horizontal lane lines (eg. stop lane lines).
Because we use Hough line transform, it will be required that we relax line acceptance critera to be able to capture curved lane lines. This will come at the cost of detecting more false-positives.
**Note:** I have assumed that the left lanes have negative slopes and right lanes have positive slopes. This makes the algorithm more robust at the cost of loss of generality.
## Possible improvements
* The use of previous frames in video to predict the new position of lanes. The prediction can be compared to the current detected lane to check for wrong lane detections.
## Optional Challenge
The optional challenge is not solved yet. Hope it will be done in the near future!

[Video-1]: <https://github.com/MChehadeh/userTerminal/blob/master/Button-Upload-icon.png>
[Video-2]: <https://github.com/MChehadeh/userTerminal/blob/master/Button-Upload-icon.png>