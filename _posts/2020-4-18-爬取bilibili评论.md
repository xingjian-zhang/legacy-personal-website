---
layout:     post
title:      爬取bilibili评论
subtitle:   使用bilibili API
date:       2020-4-18
author:     JIM
header-img: img/post-bg-coffee.jpg
catalog: true
tags:
    - Python
    - JSON
    - 爬虫
    - NLP
---

# 闲着没事爬了一下批站

去网上搜了一下B站的API，发现虽然没有官方文档，但有的竟然能用，而且访问限制也很松。于是尝试爬取了一些视频的评论区。

爬取评论区的API如下

```text
https://api.bilibili.com/x/v2/reply?jsonp=jsonp&pn=1&type=1&oid={av}&sort=0
```
封装了一个对象，目前可以指定AV号爬取评论，以后再更新指定UP主...源代码见末尾

以[黑人抬棺原视频](https://www.bilibili.com/video/BV1NZ4y1j7nw)为例，其AV号为370186695。

输入：

```python
from bilibili_spider import BilibiliSpider
import count_frequency

spider = BilibiliSpider()
spider.set_aid(370010949)
spider.collect()
```
输出：
```cmd
Loading...816/816
```

统计一下高频词，输入：

```python
reply = ' '.join(spider.data)
count_frequency.word_freq_stat(reply, 20)
```

输出：

```
2121	doge
1954	人
1627	笑
1594	专业
1164	死
1155	抬
1100	棺材
1016	棺
757		哭
750		视频
714		看
660		黑哥
654		好
648		抬棺
570		想
556		系列
548		热词
539		播放
538		走
530		生死
```

源代码

```python
import requests
import json


class BilibiliSpider:
    def __init__(self):
        self.aid = 0
        self.size = 0
        self.api = 'https://api.bilibili.com/x/v2/reply'
        self.data = []

    def set_aid(self, aid):
        self.data = []
        self.aid = aid
        self.totalpage = self._set_totalpage()

    def _get_reply(self, pn):
        _para = {
            'jsonp': 'jsonp',
            'pn': str(pn),
            'nohot': '1',
            'type': '1',
            'oid': str(self.aid),
            'sort': '1'
        }
        _data = requests.get(self.api, params=_para).json()
        if _data is not None:
            return [reply['content']['message'] for reply in _data['data']['replies']]
        else:
            return []

    def _set_totalpage(self):
        _para = {
            'jsonp': 'jsonp',
            'nohot': '1',
            'pn': 1,
            'type': '1',
            'oid': str(self.aid),
            'sort': '1'
        }
        _data = requests.get(self.api, params=_para).json()
        return _data['data']['page']['count'] // 20

    def collect(self):
        for pn in range(1, self.totalpage + 1):
            print('\rLoading...' + str(pn) + '/' + str(self.totalpage), end='')
            self.data += self._get_reply(pn)

```


