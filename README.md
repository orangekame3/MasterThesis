# ms
 
坂田さんのdockerfileを使ってtex環境を作る。

まずは坂田さんのリポジトリからdockerfileをプルしてくる。
``` bash
docker pull squary/alpine-texlive
```
その次に


下の設定をVScodeのsetting.jsonに加える
``` json
"latex-workshop.latex.recipes": [
    {
        "name": "compile",
        "tools": [
        "ptex2pdf"
        ]
    }
    ],
    "latex-workshop.latex.tools": [
    {
        "name": "ptex2pdf",
        "command": "docker",
        "args": [
        "run",
        "--rm",
        "-v",
        "C:/Users/miyao/ms:/workdir",
        "squary/alpine-texlive",
        "ptex2pdf",
        "-l",
        "/workdir/%DOCFILE_EXT%"
        ]
    }
    ],
"latex-workshop.latex.autoBuild.run": "onFileChange",
"latex-workshop.docker.enabled": true,
"latex-workshop.view.pdf.viewer": "browser"
```


"C:/Users/miyao/ms:/workdir",をtexファイルがおいてあるところを指定する。

これで、度々どのイメージを使用するかということをコマンドで指定する必要がなくなる。
ただ、dockerが正常に起動していることは確認しておくこと。

packageは一通りインストールされているみたいだが、一気に実行しようとするとエラー吐く。よくわからない。
新しくパッケージをインストールしようとするとtlmgrコマンドが古くて使えないと怒られる。




