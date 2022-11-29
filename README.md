# 高頻罕見事件分析-APPLE股票數據

👋
## Abstract
在這項工作中，我們提出了一種檢測罕見事件的方法，這些罕見事件是定義為相對於交易量的較大價格變動。我們分析
檢測到這些罕見事件后的公平行為。我們提供根據這些事件的檢測來校準交易規則的方法，以及說明特定交易規則。我們將該方法應用於即時報價數據
在五天內購買數千隻股票。為了得出全面的結論，我們將股票分組，並計算每個類別在這些罕見事件之後價格回升的概率。我們開發的方法基於非參數統計，並使
沒有關於研究中隨機變數分佈的假設
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

<br>-**for迴圈**
```python
for i in <some list>:
 <do something for each i here>
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
