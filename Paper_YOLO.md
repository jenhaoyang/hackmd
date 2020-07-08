###### tags: `paper`
# YOLO Paper
## 簡介
### 優點
1. 速度快
2. 相較於Fast RCNN，將背景誤判成目標的機率降低。因為YOLO是用整張圖片去學習而不是用濾鏡
3. YOLO辨識畫中物體的能力更強，因為YOLO能夠學到一個物體的概誇外貌

### 劣勢
比起頂級的物件偵測系統，YOLO的準確率還是不及他們
YOLO雖然可以快速識別物體，但是在標註它們的位置的時候並不準確，尤其是小物體


### Intersection over Union (IoU)
通常IoU>0.5可以視為好的預測
![](https://i.imgur.com/gpGHciY.png)

### 方法介紹
YOLO將傳統物件偵測方法中分散的元件統一到一個神經網路去處理。

神經網路從來自整張圖中的特徵來預測每一個bounding box，同時他也預測所有類別的bounding box

1. 系統將輸入的圖片切割成$S\times S格子$,如果物件的中心點落在格子中心，這個格子就負責偵測該物件
2. 每個格子預測$B$個bounding boxes和對於這些bounding boxes 的confidence分數
    這些confidence分數反映模型對於"包含一個物件"和"這個bounding box框住物件的準度"，confidence寫為$Pr(Object)* IOU^{truth}_{pred}$，如果沒有東西在這個格子裡面，confidence為0,否則我們希望confidence等於IOU
3. 每個bounding box包含5個參數,x,y,w,h,confidence,(x,y)代表box的中心==相對於一開始切出來的格子(grid cell)的邊界,寬(w)和高(h)的預測是相對於原圖的寬和高,confidence 則是預測bound box 和實際物件框的IOU==
4. 每一個格子(gtid cell)也預測這個自己這格可能是什麼物體，如果預測的物體有五種類型，C就是一個五個元素的向量，這個預測跟bounding box 的數量沒有關係
5.  





#### 相關資源

##### 文章
- [ ] 1. Understanding YOLO https://hackernoon.com/understanding-yolo-f5a74bbc7967
- [ ] 2. 你真的读懂yolo了吗？ https://zhuanlan.zhihu.com/p/37850811
- [ ] 3. 深度學習-物件偵測YOLOv1、YOLOv2和YOLOv3 cfg 檔解讀(一) https://medium.com/@chih.sheng.huang821/%E6%B7%B1%E5%BA%A6%E5%AD%B8%E7%BF%92-%E7%89%A9%E4%BB%B6%E5%81%B5%E6%B8%ACyolov1-yolov2%E5%92%8Cyolov3-cfg-%E6%AA%94%E8%A7%A3%E8%AE%80-75793cd61a01


##### 程式
https://github.com/pjreddie/darknet