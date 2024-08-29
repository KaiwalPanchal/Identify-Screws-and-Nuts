# Identify-Screws-and-Nuts

- **Objective**:
    - Develop an automated system to accurately count screws and nuts in an image using computer vision techniques.
    
- **Image Preprocessing**:
    - **Channel Selection**: Extracted the V (value) channel from the HSV color space, which represents the brightness of the image, making it suitable for further processing.
	
- **Initial Thresholding**:
    - **OTSU Thresholding**: Applied OTSU's method to automatically determine the optimal threshold value, converting the V channel image into a binary image where screws and nuts are highlighted.
    
- **Inversion**:
    - **Binary Inversion**: Inverted the binary image, making the screws and nuts appear as black objects on a white background, which is beneficial for the next steps.
    
- **Distance Transformation**:
    - **Distance Transform**: Computed the distance transform of the binary image to emphasize the central parts of the objects, aiding in distinguishing individual objects that are close to each other.
    
- **Secondary Thresholding**:
    - **OTSU Thresholding (again)**: Reapplied OTSU’s method on the distance-transformed image to further refine object detection by creating more defined object boundaries.
    
- **Second Distance Transformation**:
    - **Distance Transform**: Performed a second distance transformation to accentuate the separation between closely packed objects, ensuring accurate counting.
    
- **Final Thresholding and Inversion**:
    - **Final OTSU Thresholding**: Applied OTSU’s method one more time to finalize the object contours, followed by binary inversion if necessary, to prepare for contour detection.
    
- **Contour Detection**:
    - **Finding and Filtering Contours**: Used `cv2.findContours()` to detect contours, filtering them based on size and shape to differentiate between screws and nuts.
    
- **Object Counting**:
    - **Classification and Counting**: Classified objects based on their contours and counted them separately as screws and nuts.
    
- **Validation**:
    - **Accuracy Check**: Compared the automated counts with manual counts to ensure accuracy and fine-tuned the parameters as needed.
    
- **Implementation**:
    - Integrated the method into an automated pipeline for counting screws and nuts in various images, with potential applications in inventory management or quality control.
