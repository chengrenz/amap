# com.kit.cordova.amapnavigation

使用高德地图sdk进行导航

## 安装
`cordova plugin add https://github.com/chengrenz/amap  --variable iosamapkey=f81f461e33d304b1fab5765af9a7a8ce --variable androidamapkey=5ef4a68fc22c34a2d800235ebd1322f4 `



### ionic1调用方法

```js
var successCallback = function(message){
  //do something
};

var errorCallback = function(message){
    console.log(message);
};

cordova.plugins.AMapNavigation.navigation({
   lng: 起始地的经度,
   lat: 起始地的纬度
}, {
    lng: 终点的经度,
    lat: 终点的纬度
}, NavType //导航类型，0为实时，1为模拟
,successCallback, errorCallback);

```

### ionic2调用方法

```
import {Injectable} from '@angular/core';
declare var AMapNavigation;

@Injectable()
export class NativeService {
  constructor() { }
  /**
   * 地图导航
   * @param startPoint 开始坐标
   * @param endPoint 结束坐标
   * @param type 0实时导航,1模拟导航,默认为模拟导航
   * @return {Promise<string>}
   */
  navigation(startPoint, endPoint, type = 1): Promise<string> {
    return new Promise((resolve) => {
      AMapNavigation.navigation({
        lng: startPoint.lng,
        lat: startPoint.lat
      }, {
        lng: endPoint.lng,
        lat: endPoint.lat
      }, type, function (message) {
        resolve(message);
      }, function (err) {
        alert('导航失败:' + err);
      });
    });
  }
}

```