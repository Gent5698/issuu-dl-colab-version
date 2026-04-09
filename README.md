# issuu-dl

issuu-dl 用於從 [issuu.com](https://issuu.com) 下載文件。它會將文件的每一頁下載為 JPG 格式，並儲存在 /tmp 的暫存目錄中（圖片不會被刪除）。之後這些圖片會被轉換成 PDF，並儲存在當前目錄，檔名為文件標題。

## 使用方式

```
./issuu-dl <issuu.com 上的雜誌/書籍 URL>
```

URL 必須是整本文件的連結，例如：
https://issuu.com/jmadler/docs/modern_perl

不能是單一頁面的 URL。

你可能需要修改 ImageMagick 的設定。Linux 中的檔案位置為：

/etc/ImageMagick-6/policy.xml

請取消註解以下設定，或將權限設為 rights="read|write"：

```
<policy domain="coder" rights="none" pattern="PDF" />
```

並提高磁碟快取使用量，例如設定為 8GiB：

```
<policy domain="resource" name="disk" value="8GiB"/>
```

## 相依套件

- wget
- ImageMagick（convert）

## 移動 policy.xml 檔案到 ImageMagick-6

搭配 ImageMagick 使用：

```
mv -f ./issuu-dl/policy.xml /etc/ImageMagick-6/policy.xml
```
