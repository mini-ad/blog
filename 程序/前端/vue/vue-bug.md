
### `vue` 引入

```html
<script src="https://unpkg.com/vue@2.6.14/dist/vue.js"></script>

<link rel="stylesheet" href="//unpkg.com/element-plus/dist/index.css" />
<script src="//unpkg.com/vue@3"></script>
<script src="//unpkg.com/element-plus"></script>
```

### `v-for` 中 `index` 的 `bug`

```html
<ul>
    <li v-for="(item,index) in list" :key="index">
        <input />
    </li>
</ul>

<button @click="list.splice(0,1)">删除</button>

<script>
    list:[{id:1,name:'id1'},{id:2,name:'id2'},{id:3,name:'id3'}]
</script>
```

给 `input` 里手动输入 `1、2、3` 后，点击删除按钮，会删除第三个。因为 `diff` 算法会比较 `key` ，当它不变时 `dom` 元素会复用，导致不删除直接复制。
