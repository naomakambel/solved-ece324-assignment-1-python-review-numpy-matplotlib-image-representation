Download Link: https://assignmentchef.com/product/solved-ece324-assignment-1-python-review-numpy-matplotlib-image-representation
<br>
<h1>1         Coding &amp; NumPy Exercise</h1>

The purpose of this section is to get you re-used to the basics of Python, and the use of helpful Python libraries. In the first part of the assignment, you will be manipulating arrays using NumPy input functions, computing with arrays using for-loops, and then doing the same thing using the built-in NumPy functions. You will need the files matrix.csv and vector.npy which can be found where you downloaded this assignment.

Write a Python program in the file part1.py to accomplish the following tasks:

<ol>

 <li>Load the csv file into a NumPy array variable called matrix, using the numpy.loadtxt function.</li>

 <li>Load the npy file into a NumPy array variable called vector, using the numpy.load function.</li>

 <li>Perform matrix multiplication: output = matrix×vector using for loops to iterate through the column and rows. Do not use any built-in NumPy functions. Save output variable into a <strong>CSV </strong>file called csv using numpy.savetxt.</li>

 <li>Perform matrix multiplication:output_2 = matrix × vector by using the built in NumPy function dot. Save output_2 variable into a <strong>NumPy Array </strong>(.npy) file called output_dot.npy using numpy.save.</li>

 <li>As a way to test for consistency, make sure that the outputs match by computing the difference between output and output_2 and saving it into a CSV file called csv.</li>

</ol>

<strong>Answer the following question: </strong>If the two files you compared above are the same, does it prove that your code is correct? Explain your answer.

<h1>2         Callable Objects</h1>

A useful programming concept that is used extensively in this course is a <em>callable object</em>. A callable object is any object that can be called like a function. In Python, any object whose class has a __call__ method will be callable. For example, we can define an AddConst class that is initialized with a value val. When the object of the AddConst class is called with input, it will return the sum of val and input:

<table width="623">

 <tbody>

  <tr>

   <td width="623">class AddConst(object):def __init__(self, val): self.val = valdef __call__(self, input):return self.val + inputfoo = AddConst(4) foo(3) # Output: 7</td>

  </tr>

 </tbody>

</table>

You can think of the syntax foo(3) as a short form for foo.__call__(3).

In this second part of the assignment, you will implement several callable classes to emulate a layer in a neural network. Each class will implement a function that is parameterized by the object’s initialization parameters. Figure 7 illustrates this diagram.

Figure 7: A Callable Class initialized with parameters; it is used to call on an input to produce and output. In the AddConst class example, the initialization parameter is val and the input (when called) is the scalar value 4 with the scalar output 7

Create a Python program part2.py to accomplish the following tasks. Your implementation should be able to handle both Python scalars (int/float) or NumPy arrays (of arbitrary dimensions) as inputs:

<ol>

 <li>Create a callable object class ElementwiseMultiply that is initialized with weight, a numpy array (with 1-dimension). When called on input of the same shape as weight, the object will output an elementwise product of input and weight. For example, the 1st element in the output will be the product of the first element of input and the first element of weight.</li>

 <li>Create a callable object class AddBias that is initialized with bias, a scalar number. When called on input, the object will output the sum of input and bias. Note that input can be a numpy array, so the same bias value is added to all elements of input.</li>

 <li>Create a callable object class LeakyRelu that is initialized with alpha, a scalar value. When called on input, which may be a NumPy array, the object will output:</li>

</ol>

(1)

<em>Hint</em>: You can use NumPy functions to help you implement this class without using any for-loops. Refer to the numpy.where function.

<ol start="4">

 <li>Create a callable object class Compose that is initialized with layers, which is a list of callable objects (like those described above) that take in one parameter when called. The object Compose will compute the first ’layer’ function on the input parameter, and then the second and so on, producing an output that is a composition of object calls in layers. The order of the computations is in the order given in layers.</li>

 <li>To test your code from above, run py using either command line (python part2_test.py) or through PyCharm (right click on the part2_test.py script in the project tree and click ‘Run ‘part2 test”. What is the output in the terminal?</li>

</ol>

<h1>3         Image Processing</h1>

A picture or image can be represented as a NumPy array of “pixels”, with dimensions <em>H </em>×<em>W </em>×<em>C</em>, where <em>H </em>is the height, <em>W </em>is the width, and <em>C </em>is the number of colour channels.

Figure 8 illustrates the coordinate system. The origin is at the top left corner, and the first dimension indicates the <em>Y </em>(row) direction, while the second dimension indicates the <em>X </em>(column) dimension. Typically we will use an image with channels that give the the <strong>R</strong>ed, <strong>G</strong>reen, and <strong>B</strong>lue “level” of each pixel, which is referred to with the short form <strong>RGB</strong>. The value for each channel ranges from 0 (darkest) to 255 (lightest). However, when loading an image through Matplotlib, this range will be scaled to be from 0 (darkest) to 1 (brightest) instead, and will be a real number, rather than an integer.

You will write Python code to load an image and perform several manipulations to the image and visualize their effects. You’ll need to get the file pink_link.png from the same place you downloaded this assignment. Save the output images in the <strong>same directory </strong>as the Python file that you will be implementing.

<h2>3.1        Python Program Specification</h2>

Implement a Python program in part3.py to accomplish the following tasks:

<ol>

 <li>Load the image png into the variable img, using the pyplot.imread function from matplotlib. You can assume that the image file is located in the same directory as the Python part3.py file.</li>

 <li>Visualize the image by using the imshow function. To make the plot appear on the screen until you dismiss it, also use the pyplot.show function.</li>

</ol>

Figure 8: The image coordinate system

<ol start="3">

 <li>Modify the image by adding a constant value of 0<em>.</em>25 to each pixel in the img and store the result in the variable img_add. Note that, since the range for the pixels needs to be between [0<em>,</em>1], you will also need to implement a “clip” function on the image, where any value in the image that is outside of the desired range to the closest endpoint. You can use the numpy function clip to do this. Save the resulting image in a <strong>PNG </strong>file called img_add.png in the same directory as the part3.py Python file, using the function pyplot.imsave.</li>

 <li>From the original image, create three images that separate out the three colour channels (red, green and blue), saving each as png,img_chan_1.png,img_chan_2.png. <em>Hint</em>: First create an array initialized with zeros, then copy over the specific channel’s 2D content from img.</li>

 <li>Convert the original image to a grayscale image. In a grayscale image, the pixel value of the 3 channels will be the same for a particular <em>X,Y </em> The equation for the pixel value [1] is given by:</li>

</ol>

<em>p </em>= 0<em>.</em>299<em>R </em>+ 0<em>.</em>587<em>G </em>+ 0<em>.</em>114<em>B                                    </em>(2)

Where the <em>R,G,B </em>are the values for each of the corresponding channels. We will do this by creating an array called img_gray with the same shape as img. Save the output image in a file called img_gray.png.

<ol start="6">

 <li>Crop the image to be the <strong>top half </strong>of the image. Save the output image in a file called png.</li>

 <li>Flip the original image vertically – that is flip it about a horizontal line that is half-way down the image. Save the flipped image to the file png.</li>

</ol>

<h2>3.2        Qualitative Questions</h2>

Answer the following qualitative questions in assign1.pdf:

<ol>

 <li>How does the image png differ from the original image? What would happen if we had subtracted 0<em>.</em>25 from the original image instead of adding?</li>

 <li>Describe your programming experience in a few paragraphs. This can include the courses you have taken here at UofT, but if you have more experience, describe that as well.</li>

 <li>Describe your experience with Assignment 1: how clear were the installation instructions and questions? How can we make it more helpful?</li>

</ol>