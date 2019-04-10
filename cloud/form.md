# フォームライブラリ

## 目的

Django + Cloud Datastore + GAEの構成でフォームライブラリの選定

## 候補
 - [forms.ModelForm](https://docs.djangoproject.com/en/2.2/topics/forms/modelforms/#django.forms.ModelForm)
 - [forms.Form](https://docs.djangoproject.com/en/2.2/ref/forms/api/#django.forms.Form)

## 結論

`forms.Form` ?

## 理由

ORMを使えないのでModelと独立したFormクラスを使うのが良さそう

## 調査メモ

### GCPの情報
https://cloud.google.com/python/django/
 - Cloud DatastoreをDjangoのORMから使うことはできない
 - Cloud Datastore用のORMを提供する、Djangae というサード製品はあるが、GCPとして公式にはサポートしていない。

### djangae
https://djangae.org/
https://github.com/potatolondon/djangae

Django + GAE + Datastoreの構成でORMが使える。

### AWSの例

DjangoでDynamoDBを使うならboto3でアクセス
https://stackoverflow.com/questions/11216187/is-there-a-good-database-backend-in-django-for-amazon-dynamodb
