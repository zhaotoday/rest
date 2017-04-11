## 介绍
基于 axios 的 RESTful HTTP 简单封装，提供更人性化的 API。

## 下载
```bash
$ git clone git@github.com:zhaotoday/rest.git
```

## 使用
继承 REST
```js
class extends REST {
  constructor () {
    super()

    this.baseURL = consts.ARTICLE_API
    this.version = 'v0.1'
    this.path = 'articles'
    this.headers = {
      authorization: 'abc'
    }
  }
}
```

