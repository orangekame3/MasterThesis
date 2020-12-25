# ms

坂田さんのdockerfileを使ってtex環境を作る。

まずは坂田さんのリポジトリからdockerfileをプルしてくる。

``` bash
docker pull orangekame3/docker-alpine-texlive
```

その次に
下の設定をVScodeのsetting.jsonに加える

``` json
"latex-workshop.latex.recipes": [
        {
          "name": "latexmk",
          "tools": [
              "latexmk"
          ]
      }
      ],
      "latex-workshop.latex.tools": [
        {
          "name": "latexmk",
          "command": "docker",
          "args": [
            "run",
            "--rm",
            "-v",
            "C:/Users/miyao/Desktop/MasterThesis:/workdir",
            "orangekame3/docker-alpine-texlive",
            "latexmk",
            "-l",
            "/workdir/%DOCFILE_EXT%"
          ]
        },
      ],
      "latex-workshop.latex.autoBuild.run": "onFileChange",
      "latex-workshop.docker.enabled": true,
      "latex-workshop.latex.outDir":".tmp/",
      "latex-workshop.view.pdf.viewer": "external",
      "latex-workshop.view.pdf.external.viewer.command":
              "C:\\Program Files\\SumatraPDF\\SumatraPDF.exe",
      "latex-workshop.view.pdf.external.viewer.args": [
              "-reuse-instance",
              "%PDF%"
      ],
      "latex-workshop.view.pdf.external.synctex.command":
              "C:\\Program Files\\SumatraPDF\\SumatraPDF.exe",
      "latex-workshop.view.pdf.external.synctex.args": [
              "-reuse-instance",
              "-forward-search",
              "%TEX%",
              "%LINE%",
              "%PDF%"
],
```

"C:/Users/miyao/ms:/workdir",をtexファイルがおいてあるところを指定する。

これで、度々どのイメージを使用するかということをコマンドで指定する必要がなくなる。
ただ、dockerが正常に起動していることは確認しておくこと
