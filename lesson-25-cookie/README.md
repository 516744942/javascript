### 客户端存储
1. cookie
2. 浏览器存储api
3. indexedDB

#### 服务器在响应HTTP请求时, 通过发送Set-cookie HTTP头部包含回话信息
1. Set-Cookie: name = value
2. HTTP头部 cookie 再将他们发回服务器 Cookie:name =value


#### 限制
1. cookie 是与特定域绑定的
2. 他会与请求一起发送到创建它的域,不被其他域访问
3. 存在客户端机器上,保证它不会被恶意利用,在客户端加限制,同时cookie也不会占用大多磁盘空间

1. 不超过300个cookie
2. 每个cookie 4k(4096字节)
3. 每个域不超过20个cookie
4. 每个域名不超过81920字节(20*4*1024)
5. 超过了 浏览器就会删除之前的cookie
6. 一个字符 一个字节  多个字符  中午2个字节 em表情 4个字节s

#### cookie构成

1. 名称(name):唯一标识cookie的名称(不区分大小写)(必须经过url编码)
2. 值(value):(必须经过url编码)
3. 域(Domain):有效的域。发送到这个域的所有请求都会包含对应的cookie (www.wrox.com)表示对所有的子域有效 
4. 路径(path):请求路径包含这个路径才会把cookie 发送到服务端
5. 过期时间(expires/max-age):表示何时删除cookie的时间戳.(默认情况下浏览器会话结束后删除所有的cookie)。也可以设置删除cookie的时间GTM格式(关闭浏览器也会保存在用户机器上)(设置成过去时间就会立即删除cookie)
6. 安全标志(secure):使用SSL安全连接情况下才会把cookie发送到服务器(即https发送 http不发送);设置时候 只要一个secure就可以了
   其他标志
7. size(大小)
8. httpOnly(仅http) 防止程序获取cookie,设置为true,js无法获取cookie,防止xss攻击
9. sameSite(同一站点)(strict lax None) 用来防止 CSRF 攻击和用户追踪 
10. sameParty
11. priority(优先权)(Low/Medium/High): 数量超出时候低优先级会优先清除


#### javaScript中的cookie
1. 获取document.cookie,使用decodeURlComponent()解码


#### 字cookie
1. 为了绕过浏览器对每个域cookie的限制,提出了子cookie的概念
2. 好处单域数限制下存储更多的数据化数据


### storage
1. 提供在cookie之外的存储会话数据的途径
2. 提供跨会话持久化存储大数量数据的机制
   

###  数据库 

#### indexedDB数据库
1. indexDB使用对象存储,而不是表格数据
2. 公共命名空间下的一组对象存储,类似NoSQL风格的实现
3. 第一步调用 indexedDB.open()方法,存在就打开,不存在的话 创建并打开,返回IDBRquest的实例,onerror和onsuccess事件处理程序
```
  let db,request,version = 1;
  request = indexedDB.open("admin",version);
  request.onerror = (event)=>{
      console.log('失败')
     alert('failed to open: ${event.target.errorCode}');
  }
  request.onsuccess = (event)=>{
    db = event.target.result
    console.log('成功',event)
    console.log('成功')
  }
```
4. 版本 因此 unsigned long long 数值, 因此不要使用小数,而要使用整数

#### 对象存储

1. 创建对象存储 
   ```
    let user = {
      username:"007",
      firstName:"James",
      lastName:"Bond",
      password:"foo",
    }
   ```
2. 可以看出user对象中 最适合作为对象存储键的username 属性 全局唯一
3. 数据库不存在,open操作会创建一个新数据库,然后触发 upgradeneeded(需要升级) 事件
4. 数据库存在,数据库存在,而你指定了一个升级版的版本号,则会立即触发 upgradeneeded 事件
   ```
    request.onupgradeneeded = (event)=>{
      const db = event.target.result;
      // 如果存在则删除当前的objectStore。测试的时候可以这样做
      // 但这样会在每次执行事件处理程序时删除已有数据
      if(db.objectStoreNames.contains('users')){
        db.deleteObjectStore('users');
      }
      db.createObjectStore("users",{keyPath:"username"})
    }
   ```
5. 第二个参数的keyPath属性表示应该应用作键的存储对象的属性名

