# pyiwara
iwaraの情報を取得、ダウンロードができます。

### 簡単な使用例

```python:sample.py
from pyiwara import Video

url="https://ecchi.iwara.tv/videos/xxxxxx"
v=Video(url)
v["Source"].download("test.mp4")
```

## 詳細

### class Video
Iwaraの動画に対する操作を行います。

##### 引数
url:str 動画のURL(https://ecchi.iwara.tv/videos/xxxxxx ,videos/xxxxxx , xxxxxx)

##### プロパティ
- url:str           URL 
- id:str            https://ecchi.iwara.tv/videos/xxxxxxのxxxxxx部分
- title:str         動画タイトル
- date:datetime     アップロード日時
*files:list[File]  ダウンロード可能なファイルのリスト Fileについては後述
*user:str          アップロード者名
*user_url:str      アップロード者のURL
*thumbnail_url:str 動画のサムネイルのURL
*likes:int         高評価数
*views:int         視聴回数
*private:bool      プライベート動画か
*comment:str       動画のコメント

##### メソッド
*damp_meta_data(path) pathで指定された動画ファイルにメタデータを付与

##### 特殊メソッド
*Video[Quality] 指定されたクオリティのファイル
*イテレータ      ファイルを順番に取り出し
*len            ファイルの数

















