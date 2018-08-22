.. for doctests
   >>> import matplotlib.pyplot as plt
   >>> plt.switch_backend("Agg")

.. _numpy_exercises:

Some exercises
==============

Array manipulations
--------------------

1. Form the 2-D array (without typing it in explicitly)::

        [[1,  6, 11],
         [2,  7, 12],
         [3,  8, 13],
         [4,  9, 14],
         [5, 10, 15]]

   and generate a new array containing its 2nd and 4th rows.

2. Divide each column of the array:

   .. sourcecode:: pycon

        >>> import numpy as np
        >>> a = np.arange(25).reshape(5, 5)

   elementwise with the array ``b = np.array([1., 5, 10, 15, 20])``.
   (Hint: ``np.newaxis``).

3. Harder one: Generate a 10 x 3 array of random numbers (in range [0,1]).
   For each row, pick the number closest to 0.5.

   - Use ``abs`` and ``argsort`` to find the column ``j`` closest for
     each row.

   - Use fancy indexing to extract the numbers.  (Hint: ``a[i,j]`` --
     the array ``i`` must contain the row numbers corresponding to stuff in
     ``j``.)


Picture manipulation: Framing a Face
------------------------------------

Let's do some manipulations on numpy arrays by starting with an image
of a racoon.  ``scipy`` provides a 2D array of this image with the
``scipy.misc.face`` function::


    >>> from scipy import misc
    >>> face = misc.face(gray=True)  # 2D grayscale image

Here are a few images we will be able to obtain with our manipulations:
use different colormaps, crop the image, change some parts of the image.

.. image:: images/faces.png
    :align: center

* Let's use the imshow function of pylab to display the image.

    .. sourcecode:: pycon

        >>> import pylab as plt
        >>> face = misc.face(gray=True)
        >>> plt.imshow(face)    # doctest: +ELLIPSIS
        <matplotlib.image.AxesImage object at 0x...>

* The face is displayed in false colors. A colormap must be
    specified for it to be displayed in grey.

    .. sourcecode:: pycon

        >>> plt.imshow(face, cmap=plt.cm.gray)    # doctest: +ELLIPSIS
        <matplotlib.image.AxesImage object at 0x...>

* Create an array of the image with a narrower centering : for example,
    remove 100 pixels from all the borders of the image. To check the result,
    display this new array with ``imshow``.
* We will now frame the face with a black locket. For this, we
    need to create a mask corresponding to the pixels we want to be
    black. The center of the face is around (660, 330), so we defined
    the mask by this condition ``(y-300)**2 + (x-660)**2``

    Change the circle to an ellipsoid.
