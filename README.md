# Car-detection-with-YOLOv2Car detector using YOLO

The main objective of the Project is to Detect object in images. I have used YOLO algorithm to detect the objects using 80 classes.

The input is a batch of image of shape (m,608,608,3). The output was a list of boundary boxes along with the recognised classes. 

Each boundary box is presented as 6 number i.e. (pc,bx,by,bh,bw,c) where c is the class number. I have used 5 anchor boxes to classify 80 different classes.

YOLO architecture was as follows
        Image ---> Deep CNN --->Encoding (m,19,19,5,85)

For simplicity, I had flattened the last two dimensions so that o/p of Deep CNN is (19,19,425). 

After that, For each box the index of the class with maximum box score was found. Than I created mask by using a threshold of 0.6. After this I was left with subset of the box that i want to keep.

Than I used Non-Max Supression and Intersection over uninon (IoU), i.e. selected the box that has highest score and computed its overlap with other boxes annd removed the boxes that overlap it more than the IoU threshold. This will remove all the boxes that have a large overlap with the selected boxes.

Only best boxes remained. After this I loaded pretrained YOLO model weights and predicted the output on the dataset using the above mentioned theory.
        
