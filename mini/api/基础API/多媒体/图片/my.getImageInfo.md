
# 简介
**my.getImageInfo** 是获取图片信息的 API。

## 使用限制

- 基础库 [1.4.0](https://opendocs.alipay.com/mini/framework/lib) 或更高版本；支付宝客户端 10.1.8 或更高版本，若版本较低，建议采取 [兼容处理](/mini/framework/compatibility)。 
- 此 API 支持个人支付宝小程序、企业支付宝小程序使用。

## 扫码体验
![|127x157](https://cdn.nlark.com/yuque/0/2021/jpeg/179989/1625191567539-f1858c43-e4a1-4140-a9fb-4bcaf76ce8b3.jpeg#align=left&display=inline&height=157&margin=%5Bobject%20Object%5D&name=1.jpeg&originHeight=157&originWidth=127&size=19988&status=done&style=stroke&width=127)

## 效果示例
![|300x540](https://cdn.nlark.com/yuque/0/2021/gif/179989/1625191577132-ffa7b7bd-5fab-4f7c-9593-37ddca3bb9ba.gif#align=left&display=inline&height=540&margin=%5Bobject%20Object%5D&name=2.gif&originHeight=540&originWidth=300&size=177212&status=done&style=stroke&width=300)

# 接口调用

## 示例代码

### .axml 示例代码
```html
<!-- API-DEMO page/API/get-image-info/get-image-info.axml-->
<view class="page">
  <view class="page-description">获取图片信息 API</view>
  <view class="page-section">
    <view class="page-section-title">my.getImageInfo</view>
    <view class="page-section-demo">
      <image src="{{src}}" onError="imageError" onLoad="imageLoad" />
      <button type="primary" onTap="getImageInfo">获取图片信息</button>
    </view>
  </view>
</view>
```

### .js 示例代码
```javascript
// .js
//网络图片路径
my.getImageInfo({
      src:'https://img.alicdn.com/tps/TB1sXGYIFXXXXc5XpXXXXXXXXXX.jpg',
      success:(res)=>{
        console.log(JSON.stringify(res))
      }
    })
//apFilePath
my.chooseImage({
      success: (res) => {
        my.getImageInfo({
          src:res.apFilePaths[0],
          success:(res)=>{
            console.log(JSON.stringify(res))
          }
        })
      },
    })
//相对路径
my.getImageInfo({
      src:'image/api.png',
      success:(res)=>{
        console.log(JSON.stringify(res))
      }
    })
```

## 入参
Object 类型，属性如下：

| **属性** | **类型** | **必填** | **描述** |
| --- | --- | --- | --- |
| src | String | 是 | 图片路径，目前支持：网络图片路径、apFilePath 路径、相对路径。 |
| success | Function | 否 | 调用成功的回调函数。 |
| fail | Function | 否 | 调用失败的回调函数。 |
| complete | Function | 否 | 调用结束的回调函数（调用成功、失败都会执行）。 |


### success 回调函数
| **属性** | **类型** | **描述** |
| --- | --- | --- |
| width | Number | 图片宽度（单位为 px）。 |
| height | Number | 图片高度（单位为 px）。 |
| path | String | 图片本地路径。 |
| orientation | String | 返回图片的方向，有效值见下表。 |
| type | String | 返回图片的格式。 |


### orientation 参数说明
| **枚举值** | **说明** |
| --- | --- |
| up | 默认。 |
| down | 180 度旋转。 |
| left | 逆时针旋转 90 度。 |
| right | 顺时针旋转 90 度。 |
| up-mirrored	 | 同 up，但水平翻转。 |
| down-mirrored	 | 同 down，但水平翻转。 |
| left-mirrored	 | 同 left，但垂直翻转。 |
| right-mirrored	 | 同 right，但垂直翻转。 |

