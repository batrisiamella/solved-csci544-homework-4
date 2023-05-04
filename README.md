Download Link: https://assignmentchef.com/product/solved-csci544-homework-4
<br>
<h1>Overview</h1>

In this assignment you will write perceptron classifiers (vanilla and averaged) to identify hotel reviews as either truthful or deceptive, and either positive or negative. You may use the word tokens as features, or any other features you can devise from the text. The assignment will be graded based on the performance of your classifiers, that is how well they perform on unseen test data compared to the performance of a reference classifier.

<h1>Data</h1>

The training and development data are the same as for <a href="http://ron.artstein.org/csci544-2020-08/coding-3.html">Codin</a><a href="http://ron.artstein.org/csci544-2020-08/coding-3.html">g</a><a href="http://ron.artstein.org/csci544-2020-08/coding-3.html"> Exercise 3</a><a href="http://ron.artstein.org/csci544-2020-08/coding-3.html">,</a> and are available as a compressed ZIP archive on <a href="http://blackboard.usc.edu/">Blackboard</a><a href="http://blackboard.usc.edu/">.</a> The uncompressed archive contains the following files:

A top-level directory with two sub-directories, one for positive reviews and another for negative reviews (plus license and readme files which you won’t need for the exercise).

Each of the subdirectories contains two sub-directories, one with truthful reviews and one with deceptive reviews.

Each of these subdirectories contains four subdirectories, called “folds”.

Each of the folds contains 80 text files with English text (one review per file).

The submission script will train your model on part of the training data, and report results on the remainder of the training data (reserved as development data; see below). The grading script will train your model on all of the training data, and test the model on unseen data in a similar format. The directory structure and file names of the test data will be masked so that they do not reveal the labels of the individual test files.

<h1>Programs</h1>

<a href="http://www.ciml.info/dl/v0_99/ciml-v0_99-ch04.pdf">The perceptron algorithms appear in </a><a href="http://www.ciml.info/dl/v0_99/ciml-v0_99-ch04.pdf">Hal Daumé III</a><a href="http://www.ciml.info/dl/v0_99/ciml-v0_99-ch04.pdf">,</a><a href="http://www.ciml.info/dl/v0_99/ciml-v0_99-ch04.pdf"> A Course in Machine Learnin</a><a href="http://www.ciml.info/dl/v0_99/ciml-v0_99-ch04.pdf">g</a><a href="http://www.ciml.info/dl/v0_99/ciml-v0_99-ch04.pdf"> (v. 0.99 draft)</a><a href="http://www.ciml.info/dl/v0_99/ciml-v0_99-ch04.pdf">, </a><a href="http://www.ciml.info/dl/v0_99/ciml-v0_99-ch04.pdf">Chapter 4: The Perceptron</a><a href="http://www.ciml.info/dl/v0_99/ciml-v0_99-ch04.pdf">.</a>

You will write two programs in Python 3 (Python 2 has been deprecated): perceplearn.py will learn perceptron models (vanilla and averaged) from the training data, and percepclassify.py will use the models to classify new data. You are encouraged to reuse <em>your own</em> code from Coding Exercise 3 for reading the data and writing the output, so that you can concentrate on implementing the classification algorithm.

The learning program will be invoked in the following way:

&gt; python perceplearn.py /path/to/input

The argument is the directory of the training data; the program will learn perceptron models, and write the model parameters to two files: vanillamodel.txt for the vanilla perceptron, and

averagedmodel.txt for the averaged perceptron. The format of the model files is up to you, but they should follow the following guidelines:

<ol>

 <li>The model files should contain sufficient information for py to successfully label new data.</li>

 <li>The model files should be human-readable, so that model parameters can be easily understood by visual inspection of the file.</li>

</ol>

The classification program will be invoked in the following way:

&gt; python percepclassify.py /path/to/model /path/to/input

The first argument is the path to the model file (vanillamodel.txt or averagedmodel.txt), and the second argument is the path to the directory of the test data file; the program will read the parameters of a perceptron model from the model file, classify each entry in the test data, and write the results to a text file called percepoutput.txt in the following format:

label_a label_b path1 label_a label_b path2

In the above format, label_a is either “truthful” or “deceptive”, label_b is either “positive” or “negative”, and pathn is the path of the text file being classified.

Note that in the training data, it is trivial to infer the labels from the directory names in the path. However, directory names in the development and test data on Vocareum will be masked, so the labels cannot be inferred this way.