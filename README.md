# libjansson[^1]
GNU Emacs30.0.50に含まれる`java/INSTALL`にしたがってパッチを適用したlibjanssonモジュールのレポジトリ。
[^1]: [2024/3/30のコミット](https://git.savannah.gnu.org/cgit/emacs.git/commit/etc/NEWS?id=1135ce461d188869e0294af45641edc2cbfacbf0)で紹介されていますが、今後はJSONのサポートにjanssonが不要になるようです(`configure`で指定しなくてもJSONは常にサポートされる)。

# 作成した手順

1. [GithubのJansson](https://github.com/akheron/jansson)をclone

```bash
$: git clone https://github.com/akheron/jansson
```

2. 2. `master`ブランチから修正用ブランチ`my/master`をcheckout

```bash
$: cd jansson
$: git checkout master
$: git checkout -b my/master
```

3. `java/INSTALL`にしたがいpatchを適用

```bash
$: patch -p1 < PATCH_FOR_JANSSON.patch
```

4. 上記patch ファイルとpatch適用後ファイルをcommitして空レポジトリにpush

```bash
$: git add -A
$: git commit -m 'nanika commit messages...'
$: gh repo create my-jansson --public
$: git remote add mine https://github.com/JIBUN/my-jansson.git
$: git branch -M my/master
$: git push -u mine my/master
```
