# python-NaiveBayesian
python implementation of a Naïve Bayesian Network - in an image segmentation example

This is an example code for Naive Bayesian implemented in python (Jupyter notebook).
This simple program was designed to perform image segmentation.
<h3>Dataset</h3>
It needs a training image (i.e. pyramid2.jpeg), a labelled image (pyramid2_label.jpeg), and a test image (pyramid1.jpeg). The 3 example images are also included in this repository.

As you can see in the labelled image, areas of the image are labelled with 3 different colors (namely Red, Green Blue).
The program will read the labels based on these 3 colors. 

<h3>Training the Naive Bayesian Network</h3>
<h4>Quantise the data</h4>
To build the Naive Bayesian Network, the program first needs to quantise the data (i.e. turning the RGB values into states, so instead of value with range 0 to 255, the pixel will have values range from 0 to 7 (i.e. 8 states/bins).
To quantise the data, I used the mean and standard deviation values of each R, G & B values. 
(i.e. quantised data=((data-mean)/(3*stdev))*no_bins+no_bins/2))
<h4>Derive the pior and likelihood probabilities</h4>
Once the training data is quantised, the prior probabilities and likelihood probabilities are then calculated from the quantised data.
𝑃(𝑅𝑒𝑑|Output)=𝑃(𝑅𝑒𝑑&Output)/𝑃(Output)
<h3>Inferencing</h3>
With a new observation (new data point), the posterior probability is calculated based on the Naive Bayesian Equation:
P(Output|Red,Green,Blue)=alpha P(Red|Output) P(Green|Output) P(Blue|Output)
The data is then labeled with the Output with the highest Posterior Probability. 
<h4>Segmenting the image</h4>
For each pixel of the test image, the R, G, B values are read as the inputs to the Naive Bayesian Network and inferencing is performed to label each pixel.
