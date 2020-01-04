# Command

* ls 目前所在路徑的檔案及資料夾
* pwd 目前的工作目錄
* echo
* touch
* mkdir
* mv

## cat

1. 顯示
2. 結合
3. 新增

```bash
cat somefile.js

cat file1.txt file2.txt file3.txt > file4.txt
cat file1.txt file2.txt file3.txt | sort > file4.txt

cat somefile > somenewfile
cat >> file4.txt
```

## tail

```bash
tail somefile
tail -f somefile
tail -n 25 somefile

tail /var/log/messages
```

## find

```bash
find path -name filename
find . -name "*.js"
```

## rm&rmdir

```bash
rm someFile

rm -rfi some-directory

# some-directory 有資料時，無法移除
rmdir some-directory
```

## [grep](http://man7.org/linux/man-pages/man1/grep.1.html)

```bash
grep "some string" file

# case-insensitive
grep -i "REact" file

# number of lines
grep -c "react" index.js
```

![grep comic](../.gitbook/assets/tu-pian.png)

## [exa](https://the.exa.website/)

```bash
exa
exa -l
exa -alh
exa --tree --level=2
```

## [wget](https://www.gnu.org/software/wget/manual/wget.html)

get files using HTTP, HTTPS, FTP, FTPS

```text
wget someurl
```

## Reference

* \*\*\*\*[**Here Are 11 Console Commands Every Developer Should Know**](https://medium.com/better-programming/here-are-11-console-commands-every-developer-should-know-54e348ef22fa)\*\*\*\*

