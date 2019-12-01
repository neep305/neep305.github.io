---
layout: post
title: 현재 일자 기준으로 특정일 경과일 구하기
subtitle: using timedelta
gh-repo: neep305/neep305.github.io
gh-badge: [star, fork, follow]
tags: [python,pandas,timedelta,datetime]
---

# 특정기간만큼 경과한 날짜 구하기
- python document link: [timedelta](https://docs.python.org/3/library/datetime.html#datetime.timedelta)

```python
import pandas as pd
from datetime import timedelta, datetime

# Define the current date
current_date = pd.DataFrame(datetime.now())

# The last date a user could lapse be included
max_lapse_date = current_date - timedelta(days=20)

# Filter condition (lapse_date가 20일보다 이전인 데이터만 필터링)
conv_sub_data = sub_data_demo[sub_data_demo.lapse_date < max_lapse_date]

# How many days passed before the user subscribed
sub_time = conv_sub_data.subscription_date - conv_sub_data.lapse_date

# Save this value in our dataframe
conv_sub_data['sub_date'] = sub_time

# Extract the days field from the sub_time
conv_sub_data['sub_time'] = conv_sub_data.sub_time.dt.days
```

# Conversion Rate Calculation

```python
# filter to users who have did not subscribe in the right window
conv_base = conv_sub_data[(conv_sub_data.sub_time.notnull()) | (conv_sub_data.sub_time > 7)]

total_users = len(conv_base)

total_subs = np.where(conv_sub_data.sub_time.notnull() & (conv_base.sub_time <= 14), 1, 0)

total_subs = sum(total_subs)

# conversion_rate 
conversion_rate = total_subs / total_users
```