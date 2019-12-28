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

# 汎用APIViewのフィールドが見たい
```
$ python manage.py shell
>>> from django.views.generic import DetailView
>>> dir(DetailView)
['__class__', '__delattr__', '__dict__', '__dir__', '__doc__', '__eq__', '__format__', '__ge__', '__getattribute__', '__gt__', '__hash__', '__init__', '__init_subclass__', '__le__', '__lt__', '__module__', '__ne__', '__new__', '__reduce__', '__reduce_ex__', '__repr__', '__setattr__', '__sizeof__', '__str__', '__subclasshook__', '__weakref__', '_allowed_methods', 'as_view', 'content_type', 'context_object_name', 'dispatch', 'extra_context', 'get', 'get_context_data', 'get_context_object_name', 'get_object', 'get_queryset', 'get_slug_field', 'get_template_names', 'http_method_names', 'http_method_not_allowed', 'model', 'options', 'pk_url_kwarg', 'query_pk_and_slug', 'queryset', 'render_to_response', 'response_class', 'slug_field', 'slug_url_kwarg', 'template_engine', 'template_name', 'template_name_field', 'template_name_suffix']
```
