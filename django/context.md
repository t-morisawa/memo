# コンテクストとは何か

## Django

テンプレート変数名をPythonオブジェクトにマッピングするための辞書

ビューファイルに書き込む。

```
context = {
    'latest_question_list': latest_question_list,
}
return HttpResponse(template.render(context, request))
```

## HTTP

リクエストヘッダーのことを「リクエストコンテクスト」と言うことがある。

`Referer` `User-Agent` など。

## AWS Lambda

ハンドラに渡されるメタデータ。関数名やメモリなどなど。
