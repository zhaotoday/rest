## 介绍
基于 axios 的 ajax 简单封装，遵循 RESTful 规范，提供更人性化的 API。

## 下载
```bash
$ git clone git@github.com:zhaotoday/rest.git
```

## 使用
继承 REST
```js
class Model extends REST {
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

获取文章列表前 10 条记录
> GET /articles?$offset=0&$limit=10
```js
new Model().GET({
  params: {
    $offset: 0,
    $limit: 10
  }
})
```

获取 ID 为 1 的文章详情
> GET /articles/1
```js
new Model().GET({
  uri: 1
})
```

获取 ID 为 1 的文章的所有作者列表
> GET /articles/1/authors
```js
new Model()
  .addPath('{article_id}/authors')
  .replace({
    'article_id': 1
  })
  .GET()
```

获取 ID 为 1 的文章的 ID 为 2 的作者详情
> GET /articles/1/authors/2
```js
new Model()
  .addPath('1/authors')
  .GET({
    uri: 2
  })
```

新增 1 篇文章
> POST /articles
```js
new Model().POST({
  data: {
    title: 'Vue',
    content: 'How to use Vue.'
  }
})
```

编辑 ID 为 1 的文章
> PUT /articles/1
```js
new Model().PUT({
  uri: 1,
  data: {
    title: 'jQuery',
    content: 'How to use jQuery'
  }
})
```

删除 ID 为 1 的文章
> DELETE /articles/1
```js
new Model().DELETE({
  uri: 1
})
```