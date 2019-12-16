# JavaScript将具有父子关系的原始数据格式化成树形结构数据(id,pid)

```
    var data = [
      { id: 2, pid: 4, text: "E[父C]" },
      { id: 1, pid: 0, text: 'A' },
      { id: 4, pid: 1, text: "C[父A]" },
      { id: 3, pid: 7, text: "G[父F]" },
      { id: 5, pid: 6, text: "D[父B]" },
      { id: 7, pid: 4, text: "F[父C]" },
      { id: 6, pid: 0, text: 'B' }
    ];

    function buildTree(obj) {
      let temp = {}
      let tree = {}
      
      obj.forEach(item => {
        temp[item.id] = item
      })

      // console.log(temp)
      for (const i in temp) {
        // 如果不是最高级
        if (temp[i].pid) {
          // 如果爸爸没儿子
          if (!temp[temp[i].pid].children) {
            temp[temp[i].pid].children = {}
          }
          temp[temp[i].pid].children[i] = temp[i]
        } else {
          tree[i] = temp[i]
        }
      }
      return tree
    }
    console.log(buildTree(data))
```
