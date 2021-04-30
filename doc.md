## 配置接口
配置接口有2个，先读第一个，第一个读取失败（超时时间3s），就读第二个。
通过配置接口，获取到H5页面地址和Api接口地址
```
https://config.xunhuan.app/app.json
https://cdn.jsdelivr.net/gh/huzhiyang1998/huzhiyang1998.github.io/app.json
```
### 配置数据
```json
{
  "h5": "https://h5.xunhuan.app",  // h5页面地址
  "api": [
    "https://api.xunhuan.app"     // api接口地址，是数组，可能有多个
  ],
  "desEncodeKey": "a077809b929b11eb84d900fff8633c98",
  "errorPage": "https://github.com/choaxx233/home/blob/main/notice.md"   // 异常页面
}
```

## Api接口地址测试
对接口地址进行测试，如果不可用，就选择下一个，如果都不可用，就通过浏览器打开异常页面

- /ping
```
{
    "message": "ok",
    "code": "OK",
    "success": true,
}
```

## 获取安卓版本信息
版本不是最新，就要求用户升级。下载显示进度条。注意设置加载动画。不要让用户重复点击。

- /api/version?device=H5
```json
{
    "message": "ok",
    "code": "OK",
    "success": true,
    "data": {
        "createdDate": "2021年1月17日 15:16:51", // 发布时间
        "forcibly": true,       // 是否强制更新
        "url": "https://xxx.pak",    // 下载地址
        "updateLog": "更新日志",  // 显示出来给用户看
        "sha256": "55555", // apk的sha256 hash值
        "version": "0.0.1" // app版本号
    }
}
```

## 最后
版本是最新，没有任何问题，就打开配置数据中的H5页面给用户使用就行
