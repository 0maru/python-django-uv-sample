# Django でWebアプリケーションを作る with uv / ruff

## uv のインストール

```
brew install uv
```

## uv でプロジェクトを作成する

```
uv init sample-app
```

```
 ├── .python-version
 ├── hello.py
 ├── pyproject.toml
 └── README.md
```

## 仮想環境を作成する

```shell
uv sync
```

.venv が作られる  
このときのPythonのバージョンはpyproject.toml のrequires-python の値が使用される。

使用するPython のバージョンも切り替えることができるので、初期設定のバージョンで不都合がある場合にはPython
のバージョンを切り替えて好きなバージョンを使用することができる。

```shell
uv python install 3.11.9
uv venv --python 3.11.9
```

pyproject.toml と .python-version の値を書き換えて使用するバージョンを指定できる。  
（コマンドから指定できそうだがわからないので手で書き換え）

使用可能なPythonのバージョンは下記のコマンドで見ることができる。

```shell
uv python list
```

## Django のインストール

uv は `uv add <package_name>` で依存関係の追加が行える

```shell
uv add Django
```

## Django のアプリを作成する

venv に入って下記のコマンドを実行してアプリを作成する。

```shell
django-admin startproject app
```

### django-admin startproject app を実行したあとのディレクトリ構造

```
├── .python-version
├── .venv
├── app
│  ├── app
│  │  ├── __init__.py
│  │  ├── asgi.py
│  │  ├── settings.py
│  │  ├── urls.py
│  │  └── wsgi.py
│  └── manage.py
├── hello.py
├── pyproject.toml
├── README.md
└── uv.lock
```

## Django のサーバを起動する

```shell
uv run python app/manage.py runserver
```
