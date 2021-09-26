Currently I've got functions that map a convolution to an equivalent dot product and back. They are in learning_kernels.ipynb.


And it's enough to optimise kernels with mini batch (currently size 1) gradient descent


Read the pdf for why questions.


Looks like this time I'll make it. It can already learn kernels.


Next step is to build an easy small test model.

    1. Let's do simple data.

        Input: 3x3 grey.

        Outputs:
            1) mostly white 
            2) mostly black

    2. Architecture.

        Kernels: 2x2x2.
        Concatenation.
        1 fully connected layer with binary cross entropy.

        Looks simple enough.
        Obviously there's no need for convolutions here. 
        But don't think they'll cause problems. 
        They'll just leran some whatewer random noise works well.
        The idea is to make a small model with easily scalable architecture that works.
        It'll also learn fast because it doesn't need many training examples and is really tiny.


    Grad descent is going to look like:
        1. Kernels.
            1) dloss_dl
            2) dl_dconcat
            3) dconcat_dk1, dconcat_dk2
            4) dloss_dk1, dloss_dk2 and optimize them
             
        2. Weights.
            1) dloss_dl
            2) dl_dW and 
            3) dloss_dW and optimize it

This stuff is in a new notebook.

I found a bug; probably it's something with overflows somewhere in numpy, but I don't know where exactly. 
Dividing all inputs by 2 solves it. Without it on some examples the kernels overfit on the opposit of what they should be. Setting exceprions/warnings in numpy doesn't seem to show anything. It could be just numerical instability in np linalg least squares. But it seems to be caused by big numbers insted of numbers near 0. 
