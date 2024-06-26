## 依赖请求

`SWR` 还允许请求依赖于其他数据的数据。当需要一段动态数据才能进行下一次数据请求时，它可以确保最大程度的并行性（`avoiding waterfalls`）以及串行请求。

```js
function MyProjects() {
  const { data: user } = useSWR('/api/user')
  const { data: projects } = useSWR(() => '/api/projects?uid=' + user.id)
  // 传递函数时，SWR 会用返回值作为 `key`。
  // 如果函数抛出错误或返回 falsy 值，SWR 会知道某些依赖还没准备好。
  // 这种情况下，当 `user`未加载时，`user.id` 抛出错误

  if (!projects) return 'loading...'
  return 'You have ' + projects.length + ' projects'
}
```
