# IF仕様

## 1. Firebase
アプリとサーバの通信は、Firebaseを利用します。  
データ送信にはFirebaseでのログインが必要です。

## 2. 測定データ
移動体で取得した測定データをサーバへ送信します。

### 2.1 送信項目
| Key | Type | Memo |
|:---|:---|:---|
| date | STRING | YYYYMMDD (パーティション) |
| time | INTEGER | 測定時間(UNIXTIME) |
| latitude | FLOAT | 緯度(-90 ~ +90) |
| longitude | FLOAT | 経度(-180 ~ +180) |
| temperature | FLOAT | 温度(℃) |
| humidity | FLOAT | 湿度(%) |
| discomfort_index | FLOAT | 不快指数 |