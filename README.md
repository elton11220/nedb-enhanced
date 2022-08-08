## The JavaScript Database

**Embedded persistent or in memory database for Node.js, nw.js, Electron and browsers, 100% JavaScript, no binary dependency**. API is a subset of MongoDB's and it's plenty fast.

**This module implements some enhancements to nedb**

> To find the API you want, please visit the original [README.md](https://github.com/louischatriot/nedb/blob/master/README.md)

## Installation, tests
Module name on npm and bower is `nedb-enhanced`.

```
npm install nedb-enhanced --save    # Put latest version in your package.json
npm test                   # You'll need the dev dependencies to launch tests
bower install nedb-enhanced         # For the browser versions, which will be in browser-version/out
```

## Dev plan
- [ ] Add support for ES Module
- [ ] Add support for TypeScript

## Differences from nedb
### Updating documents
```javascript
// Let's use a same example collection
// { _id: 'id1', points: 14 }
// { _id: 'id2', points: 16 }
// { _id: 'id3', points: 20 }
// { _id: 'id4', points: 22 }

// You can pass in a function or value for the $set field. When you pass in a function, the old value of the document will be passed for the first parameter of the function and the index of the current operation item will be passed for the second
// Pass a function into the $set field to ensure that the old value of each document can be obtained when updating it
// This operation is similar to setState in the React.js: this.setState((value) => value + 3), you can get the old value immediately
// In this example, we intend to increase the value of the points field of documents with points greater than 17 by 3
db.update({ $gt: { points: 17 } }, { $set: { points: (previous, index) => previous + 3 } } )
// We can obtain the following results through this operation:
// { _id: 'id1', points: 14 }
// { _id: 'id2', points: 16 }
// { _id: 'id3', points: 23 } <- Changed
// { _id: 'id4', points: 25 } <- Changed
```


## License

See [License](LICENSE)
