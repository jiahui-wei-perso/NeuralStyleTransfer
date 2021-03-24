Neural Style Transfer
=====================


This project is an implementation of Neural style transfer based on `Neural Patches <http://arxiv.org/abs/1601.04589>`_ algorithm (Li, 2016).

The ``cnnmrf.py`` script generates a new image by using two images as inputs, one for content and one for style. The algorithm extracts annotated patches from the style image, and incrementally transfers them over to the target image based on how closely they match.



----

1. Examples
===================

There are several examples available in the notebook, where you can directly see or re-run this algorithm.

In order to use the notebook or python script, you need download the VGG-19 model weight and place it in the same level as the jupyter or python scripts.


2. Script Parameters
----------------------

You can configure the algorithm using the following parameters. Type ``python3 doodle.py --help`` for the full list of options, or see the source code.

* ``--style-weight=50.0`` — Weight of style relative to content.
* ``--style-layers=3_1,4_1`` — The layers to match style patches.
* ``--content-weight=1.0`` — Weight of content loss.
* ``--smoothness=1.0`` — Weight of image smoothing scheme.
* ``--seed=noise`` — Seed image path, "noise" or "content".
* ``--print-every=10`` — How often to log statistics to stdout.
* ``--save-every=10`` — How frequently to save PNG into `frames`.


3. Installation & Setup
=======================
    pip install requirements.txt

If you want to transfer the style given a source style with annotations, and a target content image with annotations, you can use the following command lines.  In all cases, the semantic map is loaded and used if it's found under the ``*_sem.png`` filename that matches the input file.

    python cnnmrf.py --style data/style/style.jpg --style data/style/style.jpg \
                      --output output.png --device=cpu --phases=1 --iterations=100

You'll also need to download this `pre-trained neural network <https://github.com/alexjc/neural-doodle/releases/download/v0.0/vgg19_conv.pkl.bz2>`_ (VGG19, 80Mb) and put it in the same folder as the script to run.




