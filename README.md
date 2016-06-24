### 使用  
models/article.js:  
```js
import { REST, consts } from 'utils'

export default class extends REST {
  constructor() {
    super()
    this.baseURL = consts.API_URL
    this.version = 'v1.0'
    this.path = '/article'
  }
}
```

actions/article.js:  
```js
import actionTypes from '../consts/article'
import Model from '../models/article'
import { createAction } from 'redux-actions'

export const postArticle = createAction(
  actionTypes.POST_ARTICLE,
  (options) => {
    return new Model()
      .addPaths(['{category}', 'news'])
      .replace({
        category: 123
      })
      .POST({
        data: options.data
      })
  }
)
```
