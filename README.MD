Currently I've got functions that map a convolution to an equivalent dot product and back.


And it's enough to optimise kernels with mini batch (currently size 1) gradient descent


Read the pdf for why questions.


Looks like this time i'll make it. It can already learn kernels.


Next step is to write a nice function that differentiates a whole minibatch. 

I found a bug; probably it's something with overflows somewhere in numpy, but I don't know where exactly. 
Dividing all inputs by 2 solves it. Without it on some examples the kernels overfit on the opposit of what they should be. 

