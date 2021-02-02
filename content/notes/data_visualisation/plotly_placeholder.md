---
title: "Plotly Placeholder"
subtitle: "A placeholder note for plotly chart basics."
author: "Cam"
date: 2021-01-01
description: "A placeholder note for plotly chart basics."
summary: "A placeholder note for plotly chart basics."
type: note
categories: ["Python", "Data Visualisation"]
tags: ["charts", "plotly"]
draft: false
---

{{< toc >}}

## Installation

To install `pip install matplotlib`

## Sample Plotly Chart

Here's a sample chart from the plotly gallery.


```python
import yfinance as yf
import plotly.graph_objects as go
import pandas as pd

#from datetime import datetime
ticker = 'BTC-USD' #'TSLA'#
stock_data = yf.Ticker(ticker)

#is this adjusted?
ohlc = stock_data.history(period="max").drop(columns=['Dividends','Stock Splits'])
ohlc["EMA(50d)"] = ohlc["Close"].ewm(span=50).mean()
ohlc["EMA(200d)"] = ohlc["Close"].ewm(span=200).mean()
# need to work out how to add without affeting next step
ohlc.tail()

agg_dict={'Open': 'first',
          'High': 'max',
          'Low': 'min',
          'Close': 'last',
          'Volume': 'sum'}

weekly_ohlc = ohlc.resample('W-FRI').agg(agg_dict)

weekly_ohlc["EMA(10w)"] = weekly_ohlc["Close"].ewm(span=10).mean()
weekly_ohlc["EMA(35w)"] = weekly_ohlc["Close"].ewm(span=35).mean()

up_colour = '#3d9970' #default up / '#0080ff' is #bloomberg blue
down_colour = '#ff4136' #default down
#set up three themes? camdefault/tradethetape, yahoo, bloomberg?

candlestick = go.Candlestick(
    x=weekly_ohlc.index,
    open=weekly_ohlc['Open'],
    high=weekly_ohlc['High'],
    low=weekly_ohlc['Low'],
    close=weekly_ohlc['Close'],
    name = f'Last Price {weekly_ohlc["Close"][-1]:.2f}',
    yaxis='y2',
    increasing_line_color=up_colour,
    decreasing_line_color=down_colour
)

volume = go.Bar(
    x=weekly_ohlc.index, 
    y=weekly_ohlc['Volume'],
    yaxis='y',
    name=f'Volume {weekly_ohlc["Volume"][-1]/1000000:.1f}M',
    marker_color = [down_colour if close_minus_open < 0 else up_colour for close_minus_open in (weekly_ohlc['Close']-weekly_ohlc['Open']).tolist()]
)

ema_short = go.Scatter(
    x=weekly_ohlc.index, 
    y=weekly_ohlc['EMA(10w)'],
    mode='lines',
    name=f'EMA(10w) {weekly_ohlc["EMA(10w)"][-1]:.2f}',
    line_color ='red',
    yaxis='y2'
)

ema_long = go.Scatter(
    x=weekly_ohlc.index, 
    y=weekly_ohlc['EMA(35w)'],
    mode='lines',
    name=f'EMA(35w) {weekly_ohlc["EMA(35w)"][-1]:.2f}',
    line_color ='blue',
    yaxis='y2'
) 

layout = go.Layout(
    template='seaborn', #plotly_dark
    title = {'text': stock_data.info['shortName'], 'font': {'size': 18}},
    yaxis = {'side': 'left', 'domain': [0, 0.2], 'showticklabels': False},
    yaxis2 = {'title': f'Price ({stock_data.info["currency"]})', 'side':'right', 'domain': [0.2,  1]}, #'type': 'log', 
    hovermode='x unified',
    width=1000, height=600,
    legend = {'yanchor': 'top', 'y': 0.99, 'xanchor': 'left', 'x': 0.01},
    xaxis= {
        'range': [weekly_ohlc.index[-70], weekly_ohlc.index[-1]+(weekly_ohlc.index[-1]-weekly_ohlc.index[-2])], #default range - 70 bars adds space on right
        'rangeslider': {'visible': False},
        'rangeselector':{'buttons': [{
            'label': '1M', 'step': 'month', 'count': 1, 'stepmode': 'backward'},
            {'label': '6M', 'step': 'month', 'count': 6, 'stepmode': 'backward'},
            {'label': '1Y', 'step': 'year', 'count': 1, 'stepmode': 'backward'},
            {'label': '3Y', 'step': 'year', 'count': 3, 'stepmode': 'backward'},
            {'label': 'Max','step': 'all'}]}},
    #paper_bgcolor="LightSteelBlue",
    #utosize=True,
    margin=dict(l=60, r=60, b=60, t=75) #default seems to be 80,80,80,100
    #)
)

data = [candlestick, volume, ema_short, ema_long]
fig = go.Figure(data=data,layout=layout)

fig.write_json('candlestick.json')

#see subplots instead? can then do daily/weekly timescales?
# fix hover
```

{{< chart data="candlestick" >}} 

## References

- [venv Docs](https://docs.python.org/3/library/venv.html)
- [IPython Docs](https://ipython.readthedocs.io/en/stable/install/kernel_install.html)


```python
#Versions used in this notebook
import sys
print("OS:", sys.platform)

!python --version

from importlib.metadata import version
for library in ["jupyterlab", "plotly", "pandas", "yfinance"]:
    print(library, version(library))   
```

    OS: win32
    Python 3.9.1
    jupyterlab 2.2.0
    plotly 4.14.3
    pandas 1.2.0
    yfinance 0.1.55
    
