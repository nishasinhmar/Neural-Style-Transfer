# Neural-StyleTransfer


Image representations in a Convolutional Neural Network (CNN). A given input image is represented as a set of filtered images at each processing stage in the CNN. While the number of different filters increases along the processing hierarchy, the size of the filtered images is reduced by some downsampling mechanism (e.g. max-pooling) leading to a decrease in the total number of units per layer of the network.

Content Reconstructions. We can visualize the information at different processing stages in the CNN by reconstructing the input image from only knowing the network’s responses in a particular layer. We reconstruct the input image from layers ‘conv1 2’ (a), ‘conv2 2’ (b), ‘conv3 2’ (c), ‘conv4 2’ (d) and ‘conv5 2’ (e) of the original VGG-Network. We find that reconstruction from lower layers is almost perfect (a–c). In higher layers of the network, detailed pixel information is lost while the high-level content of the image is preserved (d,e).

Style Reconstructions. On top of the original CNN activations, we use a feature space that captures the texture information of an input image. The style representation computes correlations between the different features in different layers of the CNN. We reconstruct the style of the input image from a style representation built on different subsets of CNN layers ( ‘conv1 1’ (a), ‘conv1 1’ and ‘conv2 1’ (b), ‘conv1 1’, ‘conv2 1’ and ‘conv3 1’ (c), ‘conv1 1’, ‘conv2 1’, ‘conv3 1’ and ‘conv4 1’ (d), ‘conv1 1’, ‘conv2 1’, ‘conv3 1’, ‘conv4 1’ and ‘conv5 1’ (e). This creates images that match the style of a given image on an increasing scale while discarding information of the global arrangement of the scene.

Style transfer algorithm. First content and style features are extracted and stored. The style image a is passed through the network and its style representation AL on all layers included are computed and stored (left). The content image p is passed through the network and the content representation PL in one layer is stored (right). Then a random white noise image x is passed through the network and its style features GL and content features FL are computed. On each layer included in the style representation, the element-wise mean squared difference between GL and Al is computed to give the style loss L_style (left). Also, the mean squared difference between Fl and Pl is computed to give the content loss L_content (right).

The total loss L_total is then a linear combination of the content and the style loss. Its derivative with respect to the pixel values can be computed using error back-propagation (middle). This gradient is used to iteratively update the image x until it simultaneously matches the style features of the style image a and the content features of the content image p (middle, bottom).

Let's us make NMT more clear by the help on an example:

![neural_style_transfer_example](https://user-images.githubusercontent.com/32998362/46880539-92d1a900-ce66-11e8-9377-b138dfe16025.jpeg)

To do this, we all need to merge two images :
a “content” image (C) and
a “style” image (S),
to create a “generated” image (G). The generated image G combines the “content” of the image C with the “style” of image S.

In this example, we are going to generate an image of the Louvre museum in Paris (content image C), mixed with a painting by Claude Monet, a leader of the impressionist movement (style image S).

<img width="338" alt="louvre_generated" src="https://user-images.githubusercontent.com/32998362/46880665-ee9c3200-ce66-11e8-8a99-d52f3a9b6040.png">
