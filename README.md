⚠ **Disclaimer:** I am currently employed at CafeBazaar and I actively participate in the
interview/recruitment processes; nothing good's going to happen if we find out
you have plagiarized this work for similar tasks. So beware!

# UnsupervisedObjectLocalization
Your classification neural network for object detection and localization
<a href="https://imgur.com/deYgbSI"><img src="https://i.imgur.com/deYgbSI.jpg" title="source: imgur.com" /></a>

## Method

Guided Back-propagation has proven to be a fast and interpretable util for visualizing the parts of the image to which a specific neuron fires the most — not exactly though, just giving an insight here. This is done by gating the gradients through relu units when back-propagating from a single neuron all the way back to the input image. The idea is to make the most out of these gradients for the task of object localization when they correspond to the object. For every single image, the top neurons with the biggest positive impact on the class score, are the candidates for guided back-propagation. This top selection of neurons is done via DAM heuristic. After that, for every gradient, a saliency mask is generated by keeping pixel values that fall into a certain percentile of the gradient. These masks are separately applied on the input image and once more passed into the network, to recalculate the class scores. Neurons with the lowest classification loss, are supposed to be the ones to which the object in the image corresponds the most. The masks are finally unioned and the bounding box is simply the smallest box that encloses this area.

## This repo also contains:
  * T-SNE Representation of the Dataset
  * A Graceful Guided-Backpropagation Switch
  * I use VGG16 for the classification network

## Dataset 
I implemented this for [Divar](https://divar.ir/) image dataset, which is a C2C e-commerce platform in Iran. You can find some of these images in the below t-SNE represetation.

<a href="https://imgur.com/GM6ihcf"><img src="https://i.imgur.com/GM6ihcf.jpg" title="source: imgur.com" /></a>
