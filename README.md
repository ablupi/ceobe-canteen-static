登录npm：`npm login`，回车后会在浏览器上登录npm账号。  
npm发版：`npm publist`，需要再packag.json中更新版本号，要不然会报错。  
项目介绍：小刻食堂官网字体cdn及ios发版关联文件
关于ios发版：version.json中提供一个version字段与官网url的params中version做判断，如果相同则不显示捐赠二维码来通过ios的版本审核。  
例如：https://www.ceobecanteen.top/?version=1.0.2，而version.json中为1.0.2，此时就不会显示捐赠二维码。  
官网相关代码：
```js
if (type) {
    donateList.value = []
    axios({
        method: 'get',
        url: `https://unpkg.com/ceobe-canteen-static/version.json`
    }).then((res: any) => {
      const version = res.data.version
      donateList.value = type === version ? FOLLOW_LIST : DONATE_LIST as Array<any>
    })
  }
// FOLLOW_LIST为不展示二维码
```