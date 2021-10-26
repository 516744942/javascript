1. nodeType == 1 (元素节点Element_NODE)
2. nodeType == 2 (属性节点ATTRIBUTE_NODE)
3. nodeType == 3 (文本节点TEXT_NODE)


1. 每一个节点都有一个childNodes属性,其中包含一个NodeList的实例
2. NodeList是一个类似数组的对象,可以按位置存取的有序节点
3. 注意NodeList并不是Array实例
4. DOM结构的变化会自动地在NodeList中反映出来,是实时的活动对象
5. 可以用Array.prototype.slice.call( someNOde.childNodes,0)


### 操纵节点 
1. 所有关系节点都是只读的. 所以DOM又提供了一些操纵节点的方法
2. 常用的方法是appendChild(),用于在childNOdes列表, 返回新添加的节点  