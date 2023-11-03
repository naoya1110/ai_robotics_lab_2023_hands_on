# Remove Broken Image Files

https://github.com/naoya1110/ai_robotics_lab_2023_hands_on/blob/main/imgs/broken_image_data_error.png

If you got an error something like this, use the code below to remove broken image files from your dataset.

```
import os
import shutil
import cv2

subdirs = sorted(os.listdir("dataset"))

for subdir in subdirs:
    filenames = os.listdir(os.path.join("dataset", subdir))
    for filename in filenames:
        path = os.path.join("dataset", subdir, filename)
        img = cv2.imread(path)
        if img is None:
            try:
                os.remove(path)
                print("Removed", path)
            except IsADirectoryError:
                shutil.rmtree(path)
                print("Removed", path)
```
