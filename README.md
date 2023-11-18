## ■Colabを使う時のデータファイルをアップロードする方法

### coladでgithubファイルを開く際に、URLの前半部分[https://github.com]　を　[https://colab.research.google.com/github]　にを書き換える

例えば：

https://github.com/n-eisei/image-engineering/blob/main/8-transformation/pointcloud.ipynb
↓
https://colab.research.google.com/github/n-eisei/image-engineering/blob/main/8-transformation/pointcloud.ipynb

### エラーが出たpythonライブラリをインストールする

例えば、open3dをインストール

>!pip install open3d

## ■Colabを使う時のデータファイルをアップロードする方法

### 1.colabを使うときに、下記のコードでローカルファイルをアップロードして使う

```
from google.colab import files
def getLocalFiles():
    _files = files.upload()
    if len(_files) >0:
       for k,v in _files.items():
         open(k,'wb').write(v)
getLocalFiles()
```

#### 1.1フォルダごとにアップロードする際に、フォルダを圧縮して、data.zipをアップロードして下記コマンドで解凍。

> !unzip data.zip
> !unzip data.zip -d imgs  (既存フォルダimgsに置く）
>

### 2.colab再起動してもファイルをキープしたい方法として、gdriveにファイルを置く。

```
from google.colab import drive
drive.mount('/content/gdrive')
```

> !cp bunny.pcd /content/gdrive/MyDrive/.


### 上記の1,2は、colabの画面上にも、それぞれ
「セッションストレージにアップロード」と「ドライブをマウント」の操作ボタンがある。