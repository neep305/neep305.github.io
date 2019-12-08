---
layout: post
title: How to use Matplotlib in a web application server
subtitle: Using matplotlib in flask
gh-repo: neep305/neep305.github.io
gh-badge: [star, fork, follow]
tags: [flask,matplotlib,was,python]
---

# How to use Matplotlib in a web application server
- pyplot을 선언하지 않는다. 기본적으로 pyplot은 show()를 실행하도록 되어있고, 메모리 누수가 발생할 가능성이 있다. Matplotlib 3.1 이후 직접 Figure생성자를 선언하여 figure를 만들고, 해당 값을 인메모리 버퍼(in-memory buffer)에 저장한다.

```python
import base64
from io import BytesIO

from flask import Flask
from matplotlib.figure import Figure

app = Flask(__name__)

@app.route("/")
def hello():
   # Generate the figure **without using pyplot**.
   fig = Figure()
   ax = fig.subplots()
   ax.plot([1, 2])
   # Save it to a temporary buffer.
   buf = BytesIO()
   fig.savefig(buf, format="png")
   # Embed the result in the html output.
   data = base64.b64encode(buf.getbuffer()).decode("ascii")
   return f"<img src='data:image/png;base64,{data}'/>"
```

## 동적으로 동작하는 Matplotlib 만들기
> 링크: [여기를 클릭](http://www.dalkescientific.com/writings/diary/archive/2005/04/24/interactive_html.html)