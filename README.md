# Gain

Web crawling framework for everyone. Written with asyncio, uvloop and aiohttp.
Every could write their own web crawler easily with gain framework. Gain framework provide a pretty simple api.

## Requirements

- Python3.5+

## Installation

`pip install gain`

## Usage

Write spider.py:

```python
from gain import Css, Item, Parser, Spider


class Post(Item):
    title = Css('.entry-title')
    content = Css('.entry-content')

    async def save(self):
        with open('scrapinghub.txt', 'a+') as f:
            f.writelines(self.results['title'] + '\n')


class MySpider(Spider):
    start_url = 'https://blog.scrapinghub.com/'
    parsers = [Parser('https://blog.scrapinghub.com/page/\d+/'),
               Parser('https://blog.scrapinghub.com/\d{4}/\d{2}/\d{2}/[a-z0-9\-]+/', Post)]


MySpider.run()
```
run `python spider.py`

![](img/sample.png)

## example

the examples are in the `/example/` directory.