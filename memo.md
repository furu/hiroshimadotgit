広島git勉強会 20130601
======================

やったこと
----------

* Qiitaで tag:git log を検索して関係ありそうな記事を読んだ。
* 5Google
* 本
* 日々の鍛錬 (大嘘)


アウトライン
------------

### 自己紹介

- Twitter: @pecosantoyobe
- Github: furu
- 最近あったこと
 - ブログを作りました。IPアドレス情報です。 -> 49.212.143.129


### バージョン管理システムの目的を簡単に

- 以前の状態に戻れるように
- 変更してきた履歴を調べて、
  各々の段階で何が変わったのかを検査できるように
 - 効率良くね


### git log

- 過去を閲覧できる、もっとも基本的かつパワフルなツール、
  それが git logじゃ。
- git log は、普通 less が使われる。
- カラフルな生活を送りたい人は、`git config --global color.ui auto`
- .gitconfig
- オプションなしで実行すると、新しい順に表示される。何がや。
 - コミットログがや


### オプション

大別すると出力を制限するものと出力のフォーマットをどうするのか
というオプションがある。

#### Basic options

* --follow
 - git mv をしたときに、リネーム前の履歴もおうようにできる。
 - リネームするとその名前の履歴しか git log だけではみれない。
* --reverse
 - 逆順に表示。つまり古いものから。
* --decorate[=short|full|no]
 - ブランチ名、タグ名を表示。


#### Commit Limiting

* -<number>, -n <number>, --max-count=<number>
 - <number>分だけ表示する。
* --author=<pattern>
* --grep=<pattern>
 - コミットメッセージをgrep
 - チケットの番号 #12345
* --no-merges
 - マージコミットを除いてくれる。
* --since, --after
 - 指定した日付以降のもの。
 - 2.weeks, 2.days, '2013-06-01', '2years 1day 30minitues ago'
* --until, --before
 - 指定した日付以前のもの。
* --before, --until, --since, --after
* <path>
 - ファイルでもいいし、ディレクトリでもいい。


#### Common diff options

* -p
 - 変更した差分を表示。
 - コードレビューに便利。
* -S
 - 着目する行範囲を変更するコミットを見つける
* --stat
 - ファイル名と変更量。
 - ちょっとした統計情報
 - 変更されたファイルの概要だけ
* --numstat
 - コミットでさわったファイルの追加、削除行数を表示
* --word-diff[=<mode>]
 - 変更された単語部分のみハイライト


#### Commit Formatting

* --oneline
 - コミットIDとコミットメッセージ。
* --all
 - すべてのブランチを表示
* --pretty
* --format
 - git log = git log --format=medium (default)
 - gitconfigで変更できる。 format.pretty
* --graph
 - グラフを線とアスタリクスと色で表現してくれる。


#### History Simplification

なし

#### Diff Formatting

なし


### 見た目

- git graph

 `graph = log --graph --date-order --all
              --pretty=format:'%h %Cred%d %Cgreen%ad %Cblue%cn %Creset%s' --date=short`

- 人類の英知 alias
- おれおれ<C-h><C-h>わしわし git log フォーマット。


### 余談

#### 日報に利用する

- --author, --sinceで出力を制限する。
 - 例えば、`git log --author=furu --since=yesterday`
- mail コマンドにパイプするとか。

### 代替

- tig, gitx, gitk, 嗚呼、GUIきれいだなあ


### おわり


### リファレンス
http://git-scm.com/docs/git-log
man git-*


今回、説明しなかったオプション
--------------------------

### --log-size
ログのサイズを表示してくれる

### --relative-date
相対時間で表示してくれる。2 days ago のように。

### --date=(relative|local|default|iso|rfc|short|raw)
時間の表示の仕方を指定。

### --full-diff
git log -p <path> したときに、その<path>がコミットされたときの他のファイルのdiffも表示。

### --remotes[=<pattern>]

### --tags[=<pattern>]

### --merges
マージコミットだけ。

### --encoding[=<encoding>]
エンコーディングを指定できる。デフォルトは、utf-8

### --name-status
コミットに含まれるファイル名、変更の種別(MとかAとか)を表示。

### --summary
create mode 100644 .gitignore みたいなやつが表示されてた。

### --name-only
変更されたファイルだけ。

### --short-stat
1 file changed, 40 insertions(+)

### <revision range> 
<since>..<until>

### --branches[=<pattern>]
<pattern>が与えられなかったら--allと一緒。

## --left-right


よくわからんかったオプション
----------------------------

* -l<num>
* --source
* -m
* --first-parent
 - トピックブランチでの細かい修正をサマリ的に表示して、
   プロジェクトの変更の流れを俯瞰できる。
* --abbrev[=<n>]
* --full-history
 - Same as the default mode, but does not prune some history.


メモ
----

* 素晴しいツールがあるから、乗りかえるということもある。
* Source Tree。英(ry
* コミット数。| wc -l
 - パイプに渡すところとかどうなってんだろ
* いくつかのまとまりにしたほうがよい。
* path を指定するときは、-- が必要な場合もある。

