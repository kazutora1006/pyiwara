# pyiwara
iwaraの情報を取得、ダウンロードができます。

### 簡単な使用例

```python
from pyiwara import Video

url="https://ecchi.iwara.tv/videos/xxxxxx"
v=Video(url)
v["Source"].download("test")
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
- files:list[File]  ダウンロード可能なファイルのリスト Fileについては後述
- user:str          アップロード者名
- user_url:str      アップロード者のURL
- thumbnail:bytes   サムネイル
- thumbnail_url:str 動画のサムネイルのURL
- likes:int         高評価数
- views:int         視聴回数
- private:bool      プライベート動画か
- comment:str       動画のコメント

##### メソッド
- damp_meta_data(path) pathで指定された動画ファイルにメタデータを付与

##### 特殊メソッド
- Video[Quality] 指定された解像度のファイル
- イテレータ      ファイルを順番に取り出し
- len            ファイルの数


### class File
Videoに含まれるオブジェクトで自分で作成する必要はありません

##### プロパティ
- ext:str         ファイル拡張子 
- quality:str      動画の解像度
- url:str         動画のURL

##### メソッド
- download(path, ext:bool, meta:bool, callback:class) 
    - path 保存先
    - ext:bool ファイルに拡張子を付与するか
    - meta:bool 動画にメタデータを付与するか
    - callback 進捗を表示するためのクラス(__init__(filesize),update(size),close())が必要


### class User
Iwaraの投稿者に対する操作を行います。

#### 使用例
```python
from pyiwara import User

url = "https://ecchi.iwara.tv/users/xxxxxxx"
u = User(url)
for video in u:
    print(video.title)
```
##### 引数
url:str ユーザーのURL(https://ecchi.iwara.tv/users/xxxxxx ,/users/xxxxxx , xxxxxx)

##### プロパティ
- url:str           URL
- name:str         名前
- join:datetime     登録日
- videos:list[Video]  動画のリスト
- thumbnail:bytes   サムネイル
- thumbnail_url:str 動画のサムネイルのURL
- comment:str       概要
- urls:list[str] 動画のURLのリスト

##### 特殊メソッド
- イテレータ      動画を順番に取り出し
- len            動画の数


### class Playlist
Iwaraのプレイリストに対する操作を行います。

#### 使用例
```python
from pyiwara import Playlist

url = "https://ecchi.iwara.tv/playlist/xxxxxxx"
p = Playlist(url)
for video in p:
    print(video.title)
```
##### 引数
url:str ユーザーのURL(https://ecchi.iwara.tv/playlist/xxxxxxx ,/playlist/xxxxxxx , xxxxxx)

##### プロパティ
- url:str           URL
- title:str         プレイリストの名前
- user:str 作成者
- user_url 作成者URL
- videos:list[Video]  動画のリスト
- urls:list[str] 動画のURLのリスト

##### 特殊メソッド
- イテレータ      動画を順番に取り出し
- len            動画の数














