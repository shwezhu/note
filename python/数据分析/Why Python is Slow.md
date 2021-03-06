# Why Python is Slow: Looking Under the Hood

We've all heard it before: Python is slow.

When I teach courses on Python for scientific computing, I make this point [very early](http://nbviewer.ipython.org/github/jakevdp/2013_fall_ASTR599/blob/master/notebooks/11_EfficientNumpy.ipynb) in the course, and tell the students why: it boils down to Python being a dynamically typed, interpreted language, where values are stored not  in dense buffers but in scattered objects.  And then I talk about how to get around this by using NumPy, SciPy, and related tools for  vectorization of operations and calling into compiled code, and go on  from there.

But I realized something recently: despite the relative accuracy of  the above statements, the words  "dynamically-typed-interpreted-buffers-vectorization-compiled" probably  mean very little to somebody attending an intro programming seminar. The jargon does little to enlighten people about what's actually going on  "under the hood", so to speak.

So I decided I would write this post, and dive into the details that I usually gloss over. Along the way, we'll take a look at using Python's  standard library to introspect the goings-on of CPython itself. So  whether you're a novice or experienced programmer, I hope you'll learn  something from the following exploration.



