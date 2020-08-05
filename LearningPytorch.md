###### tags: `Pytorch`
# IBM Pytorch W1

## Tensor
建立tensor
```python
import torch
a=torch.tensor([1,2,3,4,])
a=torch.tensor([1.0,2.0,3.0,4.0],dtype=torch.int32)#指定型態

a=torch.FloatTensor([0,1,2,3])#指定型態
#類別
a.dtype #torch.int64
a.type()#torch.LongTensor
#轉型
a= a.type(torch.FloatTensor)
#尺寸
a.size()#torch.Size(5)
a.ndimension() #1維
#更改維度
a=torch.Tensor([1,2,3,4,5])#1維array
a_col=a.view(5,1)#指定維一個 5row,1 column的"二維"tensor
a_col=a.view(-1,1)#不知道有幾個元素，可以將row指定-1,pytorch會自動計算
```

#### numpy和pytorch tensor互轉
以下結果numpy_array,torch_tensor,back_to_numpy連動
![](https://i.imgur.com/8gd004T.png)

#### pandas和pytorch互轉
```python
pandas_series=Series([1,2,3,4])
pandas_to_torch=torch.from_numpy(pandas_series.values)
```
#### pytorch和python list互轉
```python
this_tensor.tolist()
```
## 每一個tensor裡面的元素也都是tensor
#### pytorch tensor元素轉換為python 數字
this_tensor[0].item()

## Product of Two Tensor z=u*v
![](https://i.imgur.com/s3qONGw.png)

## Dot Product z=u.dot(v)
![](https://i.imgur.com/0m31G7m.png)

## Universal Functions
求所有元素平均the_tensor.mean()
找最大元素max_b=b.max()
torch.sin(求所有元素平均the_tensor)#sin會套用到每一個元素
torch.linspace(-2,2,num=9)#在-2~2產生之間均勻分布的元素，產生的tensor元素總數是9
![](https://i.imgur.com/RIr8flD.png)

## 2D Tensor
每一個row是一個sample,每一個column是一個feature
![](https://i.imgur.com/tYJdDne.png)
![](https://i.imgur.com/dDOxMMh.png)
![](https://i.imgur.com/QGqvbKv.png)
![](https://i.imgur.com/n95sl8D.png)

### 2D Tensor 切割(Slice
![](https://i.imgur.com/zETIPJp.png))
![](https://i.imgur.com/rfWP7Xq.png)
### 2D Tensor 運算
![](https://i.imgur.com/Ojy4kIv.png)
![](https://i.imgur.com/gR6hdj0.png)

