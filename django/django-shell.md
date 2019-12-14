# 目的
djangoがインポートされていたり、定義したモジュールたち（主にモデル）を利用できる。

操作したり、挙動を確認するのに活用できる。

# 起動、モデル読み込み
```
$ python manage.py shell
>>> from shop.models import Book
>>> Book.objects.all()
<QuerySet [<Book: DRFの本>]>
```

# フィールドについて
Fieldクラスは基本的にはFormのフィールドとして利用されるが、直接利用することもできる。

```
$ python manage.py shell
>>> from django.forms import ChoiceField
>>> hogefield = ChoiceField(choices=[(1,'hoge'),(2,'fuga')])
>>> hogefield.clean(1)
'1'
>>> hogefield.clean(2)
'2'
>>> hogefield.clean(3)
Traceback (most recent call last):
  File "<console>", line 1, in <module>
  File "/Users/morisawa-toma/prog/drf-simplest-sample-master/venv/lib/python3.6/site-packages/django/forms/fields.py", line 149, in clean
    self.validate(value)
  File "/Users/morisawa-toma/prog/drf-simplest-sample-master/venv/lib/python3.6/site-packages/django/forms/fields.py", line 803, in validate
    params={'value': value},
django.core.exceptions.ValidationError: ['正しく選択してください。 3 は候補にありません。']
```

# HTMLでの出力を見る
これはFieldクラス単体ではできず、Formの中でfield変数を定義する必要がある。

```
$ python manage.py shell
>>> from django import forms
>>> class HogeForm(forms.Form):
...   hoge = ChoiceField(choices=[(1,'hoge'),(2,'fuga')])
...
>>> hoge_form = HogeForm()
>>> hoge_form.as_p()
'<p><label for="id_hoge">Hoge:</label> <select name="hoge" id="id_hoge">\n  <option value="1">hoge</option>\n\n  <option value="2">fuga</option>\n\n</select></p>'
```

# Enumをフィールドとして使いたい場合どうするのか
 - カスタムフィールドを作る
 - enumをchoice型にマッピングする
 - Django 3.0ではEnumのサポートが始まったらしい？
