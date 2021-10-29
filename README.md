# MediaPipePose-Estimation
## Overview
One of the applications BlazePose can enable is fitness. More specifically - pose classification and repetition counting. In this section we’ll provide basic guidance on building a custom pose classifier with the help of Colabs and wrap it in a simple fitness demo within ML Kit quickstart app. Push-ups and squats are used for demonstration purposes as the most common exercises.

![gg](https://user-images.githubusercontent.com/76062756/139408895-ff8d1558-f5a3-4924-98cb-fc318845cbef.gif)

Fig 1. Pose classification and repetition counting with MediaPipe Pose.

the k-nearest neighbors algorithm (k-NN) as the classifier. It’s simple and easy to start with. The algorithm determines the object’s class based on the closest samples in the training set.

# Classification
The k-NN algorithm used for pose classification requires a feature vector representation of each sample and a metric to compute the distance between two such vectors to find the nearest pose samples to a target one.

To convert pose landmarks to a feature vector, we use pairwise distances between predefined lists of pose joints, such as distances between wrist and shoulder, ankle and hip, and two wrists. Since the algorithm relies on distances, all poses are normalized to have the same torso size and vertical torso orientation before the conversion.


![g1](https://user-images.githubusercontent.com/76062756/139409851-f7edc29e-9dc1-44ea-ae36-258582e66a03.png)

## Repetition Counting
To count the repetitions, the algorithm monitors the probability of a target pose class. Let’s take push-ups with its “up” and “down” terminal states:

When the probability of the “down” pose class passes a certain threshold for the first time, the algorithm marks that the “down” pose class is entered.
Once the probability drops below the threshold, the algorithm marks that the “down” pose class has been exited and increases the counter.

## References 
https://google.github.io/mediapipe/solutions/solutions.html
