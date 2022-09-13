# FORENSIC DETECTION OF MEDIAN FILTERING IN DIGITAL IMAGES
---
## 1. Summary of the paper
In today’s world, due to advancement in technology and cheap hardware cost, clicking & editing photo is very common for anyone with a smartphone. Now, we have started taking photogra- phy as a proof of some incident or fact which sometimes lead to malpractices. There are many free and paid image manipulation software available to make content-preserving & content changing-manipulations. Content preserving manipulations are generally applied to conceal the trail of previous manipulations. So detection of such manipulations is highly important. Here we propose a blind forensic algorithm to detect one such content preserving manipulation which is known as median filtering (MF). Many existing anti forensic techniques depend on the assumption that there is a linear correlation between neighboring pixels which is actually destroyed by the median filter since it is a non-linear operator. So blind detection of MF be- comes highly significant in the present times. The probability of zero values on the first order difference map in texture regions is used to in detection of median filtering. Experiments have been performed to prove the high efficiency of our algorithm in blind detection of Median Filtering.
## 2. Introduction
In today’s day and age authenticity of a digital image has to be taken very seriously due to the easy availability of powerful media editing software. So Image forensic has become an art which has to be mastered in order to avoid any disastrous consequences caused by the image tampering.

Image tampering or image manipulation can be classified into two types:
1.	**Content preserving**: Only change the perceptual quality of an image
2.	**Content changing**: Changes the semantic content of the entire image
 
Although the content-preserving manipulations merely change image perceptual quality but not semantic content, such manipulations are usually applied to conceal visual trail of tampering operations to create realistic forgeries. These manipulations destroy the forensically significant fingerprints, which are left by previous tampering operations. So the existing forensic algo- rithms are bound to fail in such situations. Highly skilled forgery makers use MF to retouch the and hide the crude tampering cases. One such example is usage of MF to hide the interpo- lation traces in a new resampling algorithm which actually fools the state-of-the-art Popescue and Farid’s resampling detector. Such examples state the importance of MF detection in the image forensics field.

There are some methods which involve usage of streaking artifacts and subtractive pixel adjacency matrix (SPAM) features to detect MF in bitmap and JPEG post-compressed images, respectively. Our algorithm uses a different metric altogether which will be explained in further sections.

## 3. Problem Definition
Many of the MF detection algorithms present actually depend on an assumption that there is some linear correlation between the neighboring pixels. But median filter is a non-linear operator which actually destroys any such linear correlation which is present in an image. Below is a simple image showing how median filter destroys the linear correlation.

|Sequence|Mean|Median|
|--------|----|------|
|$X_n = 1 \space 1 \space 3$|$\frac{5}{3}$|$1$|
|$X_n = 1 \space 2 \space 0$|$1$|$1$|
|$X_n = 2 \space 3 \space 3$|$\frac{8}{3}$|$3$|

So if we consider X and Y to be neighboring signals then as we can see that after applying mean filter the linear correlation between them which is simple X+Y is preserved since mean is a linear operator. But in case of median this correlation is simply destroyed (1 + 1 != 3) This is the reason why the existing algorithms such as resampling and CFA interpolation detection which rely on the assumption of linear correlation between neighboring pixels are bound to fail. So there is a need to devise a MF detection forensic algorithm which doesn’t involve this linearity assumption.


## 4. Detection Algorithm explained

