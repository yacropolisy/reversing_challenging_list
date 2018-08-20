

strcmpでコマンドライン引数と文字列を比較してるので一発。

`Much_secure__So_safe__Wow`

`./stage1.bin Much_secure__So_safe__Wow` で実行すると、文字列が出力される。

末尾の`==` から推測できるようにbase64でエンコーディングされているのでデコードする。

```bash
./stage1.bin Much_secure__So_safe__Wow 2>&1 1>/dev/null |  base64 -d > stage1_out
```



`file stage1_out` すると、`stage1_out: POSIX tar archive (GNU)` ということなので、

`tar xvf stage1_out ` でstage2.binが手に入る。