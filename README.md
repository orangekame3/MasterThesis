# ms
 
坂田さんのdockerfileを使ってtex環境を作る。

まずは坂田さんのリポジトリからdockerfileをクローンしてくる。

その次に

''
$ docker run --rm -it -v $PWD:/workdir squary/alpine-texlive
''

$PWDをtexファイルがあるディレクトリに指定する。

packageは一通りインストールされているみたいだが、一気に実行しようとするとエラー吐く。よくわからない。
新しくパッケージをインストールしようとするとtlmgrコマンドが古くて使えないと怒られる。


特に必要ないかも知れないがvscodeのsetting.jsonを少しいじった。
''
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
''

これも冒頭と同じように"C:/Users/miyao/ms:/workdir",をtexファイルがおいてあるところを指定する。

TexとdockerのVScodeの拡張機能は個人的に便利だから入れている。


