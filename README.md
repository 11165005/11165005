# 高頻罕見事件分析-APPLE股票數據

👋
## Abstract
In this work we present a methodology to detect rare events which are 
defined as large price movements relative to the volume traded. We analyze 
the behavior of equity after the detection of these rare events. We provide 
methods to calibrate trading rules based on the detection of these events and 
illustrate for a particular trading rule. We apply the methodology to tick data 
for thousands of equities over a period of five days. In order to draw comprehensive conclusions, we group the equities into classes and calculate probabilities of price recovery after these rare events for each class. The methodology that we have developed is based on non-parametric statistics and makes 
no assumption about the distribution of the random variables in the study.
<br>-**捉歷史股價的工具**
```python
!pip install yfinance
```

<br>-**抓取AAPL一年內的資料**
```python
import yfinance as yf

msft = yf.Ticker("AAPL")

# get stock info
msft.info

# get historical market data
hist = msft.history(period="1y")
hist
```

<br>-**設定V0**
```python
#hist[["Close", "Volume"]]
V0 = hist["Volume"].mean()
amt = list(hist[["Volume"]].iloc[:, 0])
data = hist[["Close", "Volume"]]
data.head()
```

<br>-**for迴圈**
```python
data["Volume"].sum()
```

<br>-**for迴圈**
```python
data.shape
```

<br>-**for迴圈**
```python
print(data.iloc[0, 1])
print(data.iloc[-1, 1])
print(data.iloc[data.shape[0]-1, 1])
s_sum = 0
for i in range(0, data.shape[0]-1):
  s_sum = s_sum + data.iloc[i, 1]
print(s_sum)
```

<br>-**for迴圈**
```python
#for i in range(0, data.shape[0]):
 # print( int(data.iloc[j, 0]), int(data.iloc[j, 1]))
#if(s_sum < V0):
print(data.iloc[251, 0]- data.iloc[0, 0])
```

<br>**<img width="326" alt="image" src="https://user-images.githubusercontent.com/118783816/204427592-5516a7bc-14ef-4b2c-abcf-4b4900543331.png">**
```python
from pandas.core.indexes.extension import deprecate_ndim_indexing
import pandas as pd
import numpy as np

#設定一個空的k及dp, 初值皆為NaN
k = np.empty(len(hist))
dp = np.empty(len(hist))

k[:] = np.nan
dp[:] = np.nan

#將Volumn存在volume中
volume = list(hist[["Volume"]].iloc[:, 0])

#================================
#任意設定一個V0值
#================================
V0 =      np.mean(volume)

#找出每個索引值的k
for i in range(0, len(hist)):
    t=np.nan
    for j in range(i+1):
        if sum(volume[j:i]) < V0:
            t=j 
            break
    k[i]=t 

#找出每個索引值的dp
for i in range(0, len(hist)):
    t=[]
    for j in range(int(k[i]), i):
        t.append(volume[i]-volume[j])
  
    if len(t)==0:
        dp[i] = np.nan
    else:
        dp[i] = max(t)

#印dp
dp
```

<br>**<img width="374" alt="image" src="https://user-images.githubusercontent.com/118783816/204427823-8f97c0af-f6e7-4d8b-a9a4-3ad608f2fa8a.png">**
```python
#將dp(list)轉成df_dp(DataFrame)
df_dp = pd.DataFrame(dp)

#平均數/標準誤
m = float(df_dp.mean())
se = float(df_dp.std() / len(hist)**0.5)

#推論x值(假設a=0.05)
print(m-1.96*se)
```

<br>-**for迴圈**
```python
for i in <some list>:
 <do something for each i here>
```


<!--
**11165005/11165005** is a ✨ _special_ ✨ repository because its `README.md` (this file) appears on your GitHub profile.


Here are some ideas to get you started:

- 🔭 I’m currently working on ...
- 🌱 I’m currently learning ...
- 👯 I’m looking to collaborate on ...
- 🤔 I’m looking for help with ...
- 💬 Ask me about ...
- 📫 How to reach me: ...
- 😄 Pronouns: ...
- ⚡ Fun fact: ...
-->
