# 数组去重、排序、扁平化

## 去重

### 1、[...new Set(arr)]

### 2、filter + indexOf

```
function unique(list) {
    return list.filter((item, index, array) => array.indexOf(item) === index)
}

```

### 3、循环 + indexOf不存在push进新数组

```
function unique(list) {
  let arr = []
  list.forEach(item => {
    if (arr.indexOf(item) === -1) arr.push(item)
  })
  return arr
}
```

## 排序

### 1、sort

### 2、冒泡排序 =》循环，相邻两个比较，如果左边比右边大，调换位置

```
function sort1(list) {
  for (let i = 0; i < list.length; i++) {
    for (let j = i + 1; j < list.length; j++) {
      let tempi = list[i];
      let tempj = list[j];
      if (tempi > tempj) {
        arr[i] = tempj
        arr[j] = tempi
      }
    }
  }
  return list
}
```

### 3、快排，数组中间取值，遍历，比中间值小的放左边边，比中间值大的放右边，递归，concat拼接

```
function sort2(list) {
  if (list.length <= 1) return list
  var index = Math.floor(list.length / 2)
  var cur = list.splice(index, 1)
  var left = [], right = []
  for (let i = 0; i < list.length; i++) {
    const e = list[i];
    if (e < cur) {
      left.push(e)
    } else {
      right.push(e)
    }
  }
  return sort2(left).concat(cur, sort2(right))
}
```

## 扁平化

### 1、arr.toString().split(',')

### 2、循环，递归

```
// 递归
var arr = [[1, 2, 2], [3, 4, 5, 5], [6, 7, 8, 9, [11, 12, [12, 13, [14]]]], 10];
var newArr = []

function flatten(arr) {
  for (var i = 0; i < arr.length; i++) {
    instanceOf 判断
    if (arr[i] instanceof Array) {
      flatten(arr[i])
    } else {
      newArr.push(arr[i])
    }
  }
  return newArr
}
flatten(arr)
console.log(newArr)
```

