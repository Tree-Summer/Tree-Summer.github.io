---
title: LSTM
date: 2024-02-02 17:14:19
tags:
- algorithm
---
## LSTM
[一篇著名的博客](http://colah.github.io/posts/2015-08-Understanding-LSTMs/)
### 原理
LSTM有三个门，用于调节神经元信息，选择性的让信息通过<br>
门由sigmoid和神经网络层构成<br>
* 第一步：决定忘记哪些信息
* 第二步：更新
* 最后：输出

### [官方API](https://pytorch.org/docs/stable/nn.html#torch.nn.LSTM)
#### 参数
- input_size
- hidden_size
- num_layers
- bias
- batch_first
- dropout
- bidirectional
 
 #### 输入
- input(seq_len,batch,input_size)
- h_0(num_layers*num_directions,batch,hidden_size)
- c_0(num_layers*num_directions,batch,hidden_size)

#### 输出
- output(seq_len,batch,num_directions*hidden_size)
- h_n(num_layers*num_directions,batch,hidden_size)
- c_n(num_layers*num_directions,batch,hidden_size)
- 


