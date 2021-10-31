# 利用 python 將圖片轉為字串

##圖片轉為黑白
```
import numpy as np
from PIL import Image

img = Image.open(path)
limg = Image.open(path).convert('L')
```
![image](https://user-images.githubusercontent.com/93465890/139573418-55059ab6-9e99-47c4-828d-7af766b76779.png)
### 轉換後
![image](https://user-images.githubusercontent.com/93465890/139573427-21b4ed87-efbe-42f2-8f91-22e7c898d29b.png)


##圖片轉陣列，並resize
- 預設寬度為100，長度等比例縮小
```
defaultx = 100
img_array = np.array(limg)
x = img_array.shape[0] 
y = img_array.shape[1]
y2 =  y//(x//defaultx)
arr = np.array(limg.resize((defaultx, y2)))
```
###縮小後
![image](https://user-images.githubusercontent.com/93465890/139573451-b02532e8-9d1b-4e77-ad7c-6430351e5fb3.png)

##依據陣列內的值，選擇三種圖案其中一個
```
a = '●'
b = '◎'
c = '　'

array2 = []
for i in range(0, len(array)):
    strr = ''
    for j in range (0, len(array[i])):
        if array[i][j] <= 85:
            strr += a
        elif array[i][j] > 85 and array[i][j] <= 170:
            strr += b
        else:
            strr += c
    strr += '\n'
    array2.append(strr)

f = open('demo.txt', 'w')
for i in array2:
    f.write(i)
f.close()
```

##demo
![image](https://user-images.githubusercontent.com/93465890/139573527-e5170e6f-3936-4a48-b7da-3f859fd5eb86.png)
