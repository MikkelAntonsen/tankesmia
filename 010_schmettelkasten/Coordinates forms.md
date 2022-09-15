Let's clear the air of some confusion regarding bbox formats and tensor indexing.

There are two main ways of encoding bounding boxes, [x, y, x, y] and [x, y, w, h], referred to lovelingly as xyxy and xyhw. 

If an image is 128x128 pixels, the biggest xy coordinate we have is (127, 127), while the biggest, hw we have is (128, 128).

The implication is that if we want to extract a bounding box from a tensor we have to do `[y1: y1+y2+1, x1:x1+x2+1]` if we have `xyxy` bounding boxes and `[y:y+h, x:x+w]` if we have `xywh` boxes.

We see this is correct because xyxy = [0, 0, 127, 127] becomes [0:128, 0:128]

Confusingly, this means that an xyxy bounding box with coordinates [0, 0, 1, 1] actually has h,w=2, 2.