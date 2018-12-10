# Iterator函数

## Iterator是什么
- `Iterator`是一种遍历JS中的数据集合的新的方式.
- `Iterator`之所以受欢迎是因为它可以用在各种各样的场景下.

这有一个数组:
```
const authors = [
    'Neal Stephenson',
    'Arthur Clarke',
    'Isaac Asimov',
    'Robert Heinlein'
]
```
如果让你取回数组内所有的值,然后做以下的事:
- 把他们打印到屏幕上.
- 操作它们
- 在这些值上执行一些动作
如何操作? 通常,我们会想到:
- for循环
```


```
- while循环
```

```
假设我们使用一种自定义的数据结构存储这些人名,像这样:
```
const authors = {
    allAuthors: {
        fiction: [
            'Agatha Christle',
            'J.K. Rowling',
            'Dr. Seuss'
        ],
        scienceFiction: [
            'Neal Stephenson',
            'Arthur Clarke',
            'Isaac Asimov',
            'Robert Heinlein'
        ],
        fantasy: [
            'J.R.R. Tolkien',
            'J.K. Rowling',
            'Terry Pratchett'
        ]
    }
}
```
上面的`author`定义中:
- `authors`是一个对象,
  - `authors`包含另一个对象`allAuthors`
    - `allAuthors`使用三个key键('fiction','scienceFiction','fantasy')包含了三个数组
现在,请问如何实现遍历`authors`中的所有人名?
你可能会使用循环的组合来获取到这些人名.
但是,如果你这么做:
```
for (let author of authors){
    console.log(author)
}
```
你会得到:
```
TypeError: {} is not iterable
```
















