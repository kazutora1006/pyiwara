# pyiwara
iwaraの情報を取得、ダウンロードができます。

 ##簡単な使用例
from pyiwara import Video

url="https://ecchi.iwara.tv/videos/xxxxxx"
v=Video(url)
v["Source"].download("test.mp4")
