# FACE-AND-EYE-DETECTION-

USING IMAGE

Overview
Face detection is a technique that identifies or locates human faces in digital images. 
A typical example of face detection occurs when we take photographs through our smartphones, and it instantly detects faces in the picture. 
Face detection is different from Face recognition. Face detection detects merely the presence of faces in an image while facial recognition involves identifying whose face it is.

Face detection is performed by using classifiers. A classifier is essentially an algorithm that decides whether a given image is positive(face) or negative(not a face). A classifier needs to be trained on thousands of images with and without faces. Fortunately, OpenCV already has two pre-trained face detection classifiers, which can readily be used in a program. The two classifiers are:

1.Haar Classifier and
2.Local Binary Pattern(LBP) classifier.

How the algorithm works on images in steps:
1. 'Haar features' extraction
After the tremendous amount of training data (in the form of images) is fed into the system, the classifier begins by extracting Haar features from each image. Haar Features are kind of convolution kernels which primarily detect whether a suitable feature is present on an image or not. Some examples of Haar features are mentioned below:


source
These Haar Features are like windows and are placed upon images to compute a single feature. The feature is essentially a single value obtained by subtracting the sum
of the pixels under the white region and that under the black. The process can be easily visualized in the example below.


For demonstration purpose, let's say we are only extracting two features, hence we have only two windows here. 
The first feature relies on the point that the eye region is darker than the adjacent cheeks and nose region. 
The second feature focuses on the fact that eyes are kind of darker as compared to the bridge of the nose.
Thus, when the feature window moves over the eyes, it will calculate a single value. This value will then be compared to some threshold and if it passes that it will 
conclude that there is an edge here or some positive feature.

2. 'Integral Images' concept
The algorithm proposed by Viola Jones uses a 24X24 base window size, and that would result in more than 180,000 features being calculated in this window. 
Imagine calculating the pixel difference for all the features? The solution devised for this computationally intensive process is to go for the Integral Image concept. 
The integral image means that to find the sum of all pixels under any rectangle, we simply need the four corner values.

This means, to calculate the sum of pixels in any feature window, we do not need to sum them up individually. 
All we need is to calculate the integral image using the 4 corner values. The example below will make the process transparent.

3. 'Adaboost' : to improve classifier accuracy
As pointed out above, more than 180,000 features values result within a 24X24 window. However, not all features are useful for identifying a face. 
To only select the best feature out of the entire chunk, a machine learning algorithm called Adaboost is used.
What it essentially does is that it selects only those features that help to improve the classifier accuracy. 
It does so by constructing a strong classifier which is a linear combination of a number of weak classifiers. 
This reduces the amount of features drastically to around 6000 from around 180,000.

4. Using 'Cascade of Classifiers'
Another way by which Viola Jones ensured that the algorithm performs fast is by employing a cascade of classifiers. 
The cascade classifier essentially consists of stages where each stage consists of a strong classifier. 
This is beneficial since it eliminates the need to apply all features at once on a window. Rather, 
it groups the features into separate sub-windows and the classifier at each stage determines whether or not the sub-window is a face. 
In case it is not, the sub-window is discarded along with the features in that window. If the sub-window moves past the classifier, 
it continues to the next stage where the second stage of features is applied. 

Cascade structure for Haar classifiers is in OUTPUT file
