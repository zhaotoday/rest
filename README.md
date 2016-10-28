## 使用  

### redux/models/articles.js:

```js
import REST from 'utils/rest'
import consts from 'utils/consts'

export default class extends REST {
  constructor() {
    super()
    this.baseURL = consts.API_URL
    this.version = 'v1.0'
    this.path = 'articles'
    this.headers = {
      Authorization: 'abc'
    }
  }
}
```

### redux/actions/articles.js:

```js
import actionTypes from '../consts/articles'
import Model from '../models/articles'
import createAction from 'redux-actions/lib/createAction'

/**
 * 获取文章列表
 */
export const getArticles = createAction(
  actionTypes.GET_ARTICLES,
  (options) => {
    return new Model()
      .GET({
        params: options.params
      })
  }
)

/**
 * 给文章新增一个作者
 */
export const postArticleAuthor = createAction(
  actionTypes.POST_ARTICLE_AUTHOR,
  (options) => {
    return new Model()
      .addPath('{article_id}/authors')
      .replace({
        article_id: options.article_id
      })
      .POST({
        data: options.data
      })
  }
)
```

### app/index.js:

```js
this.props.getArticles({
  params: {
    title: 'the title'
  }
})

this.props.postArticleAuthor({
  article_id: 123,
  data: {
    title: 'the title'
  }
})
```
