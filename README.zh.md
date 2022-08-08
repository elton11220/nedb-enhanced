## JavaScript 数据库

**用于Node.js，nw.js、Electron和浏览器的持久化或内存数据库，100% JavaScript，无二进制依赖**。API是MongoDB的一个子集，速度非常快。

**本模块对nedb实现了一些增强功能**

> 想查看Nedb的API，请访问原始Nedb仓库的 [README.md](https://github.com/louischatriot/nedb/blob/master/README.md)

## 安装 & 测试
此模块在npm和bower的名字是 `nedb-enhanced`.

```shell
npm install nedb-enhanced --save    # 将最新版模块放进你的 package.json
npm test                        # 你将会需要dev依赖去运行测试
bower install nedb-enhanced         # 浏览器版本将会在 browser-version/out 输出
```

## 开发计划
- [ ] 添加对ES Module的支持
- [ ] 添加对TypeScript的支持

## 与Nedb的不同点
### 更新文档
```javascript
// 使用一个简单的例子
// { _id: 'id1', points: 14 }
// { _id: 'id2', points: 16 }
// { _id: 'id3', points: 20 }
// { _id: 'id4', points: 22 }

// 你可以为$set字段传入函数或值。传入函数时，将为函数的第一个参数传递文档的旧值，为第二个参数传递当前操作项的序号
// 为$set字段传递一个函数，以确保在更新文档时可以获得每个文档的旧值
// 这个操作类似于React.js中的setState：this.setState((value) => value + 3)，你可以立刻获取旧值
// 在本例中，我们打算将points大于17的文档的points字段的值增加3
db.update({ $gt: { points: 17 } }, { $set: { points: (previous, index) => previous + 3 } } )
// 我们可以通过此操作得到以下结果
// { _id: 'id1', points: 14 }
// { _id: 'id2', points: 16 }
// { _id: 'id3', points: 23 } <- 已修改
// { _id: 'id4', points: 25 } <- 已修改
```


## 许可证

查看 [许可证](LICENSE)
