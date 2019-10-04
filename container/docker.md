
# Docker

俺的ベストなPython開発環境構築方法

https://qiita.com/Tadahiro_Yamamura/items/df21487286d7cf8bfb6e

```
docker run -it -w /app -v $(pwd):/app python bash
```

- `-v, --volume` はマウント
 - `--workdir , -w` はワーキングディレクトリで、Volumeと同じにしておけばV上で作業できる
