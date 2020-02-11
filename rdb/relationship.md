
# リレーションシップ

SNSを考えてみる。

postテーブルについて考えてみると、userとpostは1対Nの関係。
 - 1つのuserはN個のpostを持つ
 - 1つのpostは1つのuserを持つ

likeテーブルについて考えてみると、userとpostはN対Nの関係？
 - 1つのuserはN個のlikeしたpostを持てる
 - 1つのpostはN個ののlikeしたuserを持てる

ここで、likeは中間テーブルというものである。

userとpostは単なる1対Nではなく、N対Nの関係も持っていると考えられる？

userとlikeは1対N、postとlikeは1対N、結果、userとpostはN対N？

# SQL

TODO

# Djangoの外部キーを考える

Djangoリレーションシップを定義するには、モデルにリレーションシップフィールドを持たせる。

 - ForeignKey
 - ManyToManyField
 - OneToOneField

通常のフィールドの代わりにこれらを持たせることでリレーションシップが生まれる。

## ForeignKey

1対Nの、N側のモデルのフィールドに、1の方のモデルの参照を定義する。

実際に登録する時はどんな感じかはまあほんとか読めば良いと思う。

## ManyToManyField

内部的に中間テーブルが作られるようになっているらしい。

中間テーブルを作成する代わりに、どちらか片方のモデルが、複数の値を持つフィールドを定義するというイメージ。

先ほどのsnsの例でいえば、likeテーブルは作らない代わりに、以下のような感じになる。

```
class Post(models.Model):
    liked_users = models.ManyToManyField(User)
```

あるいはこんな感じ

```
class User(models.Model):
    liked_posts = models.ManyToManyField(Post)
```

## OneToOneField

何かを継承する時とかに使う。

# メモ

 - リレーションシップは何と何の間にできる？
 -> フィールドからテーブルの間にできる(1対1, 1対N, N対N)

Railsの場合は多対多を定義するフィールドは存在せず、中間テーブルに相当するモデルを作ることになる様子。
