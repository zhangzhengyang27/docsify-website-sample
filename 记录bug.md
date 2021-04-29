### 1、axios post提交数据@RequestParam后端接收不到

首先要确定表单的提交类型 在main.js中配置全局默认headers:

```js
axios.defaults.headers.post['Content-Type'] = 'application/x-www-form-urlencoded';
```

确保表单提交方式为：application/x-www-form-urlencoded

然后确定数据格式应该为表单数据,建议用node的qs

```js
npm install qs --save
```

然后在main.js中　　　

```js
import Qs from "qs"
Vue.prototype.qs = Qs;　　//添加原型属性，便于全局使用
```

然后：用ｑs处理提交的数据

```js
this.$axios.post(
        '/fuck',
        this.qs.stringify({
          username:this.userName,
          password:this.password
        }),
      ).then()
```

