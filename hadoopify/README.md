Hadoopify
----------

I couldn't think of a better name for this. It came out of a discussion I had with a coworker.
He was describing a process he wanted to implement that would provide hadoop-style batching for image processing.
I'm not uber familiar with image transformation but he described a basic process, let's call it blurring.

Premise:
Given an image, devise a way to distribute "blurring" of the image across X number of worker nodes. 
The trick is that the blurring logic requires information about the subset of pixels preceeding it. For instance..

I have a square image. To "blur" a pixel in the image, I must have information about the five (5) pixels preceding it.

If my pixels are:

	blue->black->green->yellow->red->white

To properly blur the white pixel, I must take into account the previous 5 pixels (blue->black->green->yellow->red).

The same applies vertically as well.
The goal is to distribute the blurring of the entire image across 5 worker nodes in such a way that the "blurring" alogorithm is honored in the final product.
Make sense?

You don't have to use an image. In fact it's harder if you do, I think.
