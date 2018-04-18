# 中継API仕様

<span style="color: red; ">__赤文字__</span> 部分を修正してください。

## 1. JSON-RPC
```
https://{HOST}/api/v1
```

## 2. ステータス送信
ハードウェアのステータス情報を送信します。

### 2.1 リクエスト
<span style="color: red; "> __paramsは仮です。送信パラメータを記載してください。__</span>

```
{
	"jsonrpc": "2.0",
	"method": "send_status",
	"params": {
		"key1": "value1",
		"key2": "value2"
	},
	"id": 1
}
```

- 成功

```
{
    "jsonrpc": "2.0",
    "result": "OK",
    "id": 1
}
```

- 失敗

```
{
	"jsonrpc": "2.0",
	"error": {
		"code": -32600,
		"message": "Invalid Request"
	},
	"id": 1
}
```


### <h id="section2.2">2.2 データ形式</h>
__注意事項__

 - サーバ構成およびDB料金の見積もりのため、データ形式を一覧に記入してください。
 - MAX Data Sizeは、想定される最大のデータサイズを [4.1 Type凡例](#section4.1) を参考にしてください。
 - MemoにKeyの説明を記入してください。
 
#### 一覧（記入例）
<span style="color: red; ">__データ形式一覧を記入してください。__</span>

| Key | Type | Maximum Size(byte) | Memo |
|:---|:---|---:|:---|
| device_id | STRING | 52 | ハードID |
| time | FLOAT | 8 | 時間(UnixTime) |
| battery | INTEGER | 8 | バッテリー状態（%） |
| move | BOOLEAN | 1 | 0:移動中, 1:移動中 |
| latitude | FLOAT | 8 | 緯度(-90 ~ +90) |
| longitude | FLOAT | 8 | 経度(-180 ~ +180) |


## 3. 測定データ送信
センサーで測定した情報を送信します。

### 3.1 リクエスト
<span style="color: red; "> __paramsは仮です。送信パラメータを記載してください。__</span>

```
{
	"jsonrpc": "2.0",
	"method": "send_measurement",
	"params": {
		"key1": "value1",
		"key2": "value2"
	},
	"id": 1
}
```

- 成功

```
{
    "jsonrpc": "2.0",
    "result": "OK",
    "id": 1
}
```

- 失敗

```
{
	"jsonrpc": "2.0",
	"error": {
		"code": -32600,
		"message": "Invalid Request"
	},
	"id": 1
}
```

### 3.2 データ形式
__注意事項__

 - [2.2 データ形式](#section2.2)の注意事項と同じです。
 
#### 一覧（記入例）
<span style="color: red; ">__データ形式一覧を記入してください。__</span>

| Key | Type | Maximum Size(byte) | Memo |
|:---|:---|---:|:---|
| device_id | STRING | 52 | ハードID |
| measurement_id | STRING | 52 | 測定ID |
| waypoint_id | STRING | 52 | WayPointID |
| time | FLOAT | 8 | 時間(UnixTime) |
| temperature | INTEGER | 8 | 温度(℃) |
| discomfort_index | INTEGER | 8 | 不快指数 |

## 4. 参考
### <h id="section4.1">4.1 Type凡例</h>
| Tyep | Size(byte) |
|:---|---:|
| STRING | 2 + UTF-8 エンコードされた文字列のサイズ |
| INTEGER | 8 |
| FLOAT | 8 |
| BOOLEAN | 1 |
※__TIMESTAMP__は使用不可の予定です。

### 4.2 参考リンク
- [JSON-RPC](http://www.jsonrpc.org/specification)
- [Bigquery データサイズの計算](https://cloud.google.com/bigquery/pricing?hl=ja)