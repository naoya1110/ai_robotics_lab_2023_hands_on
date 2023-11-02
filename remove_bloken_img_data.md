# Remove Broken Image Files


If you got an error something like this, use the code below to remove broken image files from your dataset.

```
import os
import cv2
import shutil

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
