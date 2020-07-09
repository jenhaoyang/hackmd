###### tags: `吳恩達`
# 吳恩達 w6 機器學習實作指引

## 訓練出來的模型如果預測能力不好的解決方法

Getting more training examples
Trying smaller sets of features
Trying additional features
Trying polynomial features
Increasing or decreasing λ
這五個方法有時候測試一個就會花掉好幾個月的時間，藉由診斷方法我們可以挑出可能可以改善學習的方法

## 檢查Overfitting

### 步驟
數據資料:通常70%做訓練用，30%做測試用
訓練後的權重代入cost function得到cost function區域最小值$J_{train}(\theta)$
將測試用資料代入得到$J_{test}(\theta)$

### 測試誤差值
![](https://i.imgur.com/b7lU1Lq.png)
如果test的誤差比train的誤差還大，就有有可能是overfitting

## 模型選擇與Train/Validation/Test Sets
為了選擇適合的模型次方數，可以將訓練資料拆成Train/Validation/Test Sets
並利用以下步驟找到適合的次方數
1.用Train set算出所有候選模型的$\Theta$
2.用Validation set 來選擇最佳的模型
3.Test set 計算模型預測誤差
 generally expect $J_{\text{CV}}(\theta)$ To be lower than $J_\text{test}(\theta)$because:An extra parameter (d, the degree of the polynomial) has been fit to the cross validation set.
 
 
 ## 檢驗High bias (underfitting) 或是 High variance (overfitting)
 High bias (underfitting): both $J_{train}(\Theta)$ and $J_{CV}(\Theta)$will be high. Also, $J_{CV}(\Theta) \approx J_{train}(\Theta)$.

High variance (overfitting): $J_{train}(\Theta)$will be low and $J_{CV}(\Theta)$will be much greater than $J_{train}(\Theta)$.
 ![](https://i.imgur.com/ZG7xg60.png)

## 選擇Regularization參數$\lambda$
![](https://i.imgur.com/LWTxDJ2.png)
### 步驟
1. 建立一組$\lambda$清單
2. 將每一個$\lambda$代入有包含Regularization項的cost function
3. 將學習到的$\Theta$拿來帶入$J_{CV}(\Theta)$計算validation error，$J_{CV}(\Theta)$不包含Regularization項
4. 選擇誤差最小的$\lambda$
5. 將學習到的$\lambda$代入$J(Theta)$，並且用test set計算預測誤差

## Learning Curve
當訓練資料少的時候error模型的誤差比較小，因為模型有機會擬和全部的資料
當訓練資料越多，誤差會變大然後收斂到某個誤差值
### high bias的Learning Curve
$J_test(\Theta)$和$J_train(\Theta)$的誤差在多訓練資料的時候很接近
==這種狀況下增加更多的學習資料對於降低誤差沒有用==
![](https://i.imgur.com/ZytdmPX.png)

### high variance的Learning Curve
$J_test(\Theta)$和$J_train(\Theta)$的誤差在訓練資料少的時候離很遠，隨著訓練資料變多會慢慢接近
==增加更多的學習資料對於降低誤差會有幫助==
![](https://i.imgur.com/UDN9YSs.png)

### 判斷該用什麼方法
* Getting more training examples: Fixes high variance
* Trying smaller sets of features: Fixes high variance
* Adding features: Fixes high bias
* Adding polynomial features: Fixes high bias
* Decreasing λ: Fixes high bias
* Increasing λ: Fixes high variance.

簡單的神經網路容易有underfitting的問題，不過需要的計算資源少
大型神經網路容易overfitting，計算資源也消耗的多。可以利用 regularization (增加 λ)來處理overfitting


從一層hidden layer是一個好的開始，可以利用 cross validation set來訓練不同層樹的神經網路，並且選擇誤差最小的