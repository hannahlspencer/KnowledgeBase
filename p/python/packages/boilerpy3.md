# boilerpy3

* [PyPI](https://pypi.org/project/boilerpy3/)

Boilerpy3 is used to extract content from HTML pages, and can directly from a URL.



```
from boilerpy3 import extractors

extractor = extractors.ArticleExtractor()
doc = extractor.get_content_from_url(url)
```

Errors should be handled with a try/except, although you can also use requests for some errors:

```

resp = requests.get(url, headers=headers)
if resp.ok:
    doc = extractor.get_content(resp.text)
else:
    //something else
```
