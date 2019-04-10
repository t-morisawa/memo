# Google Cloud Functions

wsgiサーバを立てずに各FWを利用する方針で調査

[補足]Lambdaの場合はwsgiサーバをテクニカルに立てるような形で実施しているが同じ方法をCloud Functionsに適用するのは難しそう


## Flask

### リクエスト
Cloud Functionsのハンドラに渡されるrequestオブジェクトがFlaskのRequest型で来るのでそのまま使用可能

### ルーティング
デコレータをつけてもそのままでは働かない。

URLからmethodへの参照を取得するメソッドを定義することでハンドラメソッドの中でルーティングを実現できる

参考リンク
https://stackoverflow.com/questions/38488134/get-the-flask-view-function-that-matches-a-url

以下のような実装
```
import json
from flask import Flask, redirect
from werkzeug.routing import RequestRedirect, MethodNotAllowed, NotFound

app = Flask(__name__)

def get_view_function(url, method='GET'):
    """Match a url and return the view and arguments
    it will be called with, or None if there is no view.
    """

    adapter = app.url_map.bind('localhost')

    try:
        match = adapter.match(url, method=method)
    except RequestRedirect as e:
        # recursively match redirects
        return get_view_function(e.new_url, method)
    except (MethodNotAllowed, NotFound):
        # no match
        return None

    try:
        # return the view function and arguments
        return app.view_functions[match[0]], match[1]
    except KeyError:
        # no view is associated with the endpoint
        return None


def hello_world(request):
    # return redirect()
    return get_view_function(request.path)[0](request)


@app.route('/')
def index(request):
    return f'<a href="https://www.google.com/">here is index</a>'


@app.route('/hoge')
def hoge(request):
    return f'hoge!'

@app.route('/cookie')
def print_cookie(request):
    return json.dumps(request.cookies)

@app.route('/printreq')
def print_header(request):
    return str(request.headers.to_wsgi_list())
```

## Django

動かせるところまでいけず

### リクエスト

ハンドラにはflask.Request形式で渡されるので、必要に応じてDjangoのリクエスト形式に変換する必要あり

### ルーティング

そのままだとルーティングされない。

Flaskと同様、登録されたURLプールからメソッドへの参照を逆引きする関数を利用しようとしたもののやはり動かなかった（URLプールに登録できていなかった）。

```
import sys
from django.conf.urls import url
# from django.core.urlresolvers import resolve # for django 1
from django.urls import reverse
from django.conf import settings

def hoge(request):
    return 'here is hoge'

def index(request):
    return 'here is index'

urlpatterns = [
    url(r'^$', index),
    url(r'hoge$', hoge),
]

def handler(request):
    if not settings.configured:
        settings.configure(
            ALLOWED_HOSTS=["*"],
            DEBUG=True,
            ROOT_URLCONF=__name__,
            MIDDLEWARE_CLASSES=(
                'django.middleware.common.CommonMiddleware',
            )
        )

    return reverse('index')
    # return resolve('index')
```

