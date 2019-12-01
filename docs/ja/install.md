# インストール

Zettlrのインストールは簡単で、どのオペレーションシステムでも、たったの1ステップで完了します。Zettlrはクロスプラットフォームのため、お使いのシステムの種類にかかわらず動作するでしょう。Zettlrは、macOS、Windows、DebianベースとRedHatベースのLinuxシステム(Ubuntu, Gnome, Xubuntu, Kubuntu, Fedora, RedHat and the like)向けに、ビルド済みモジュールを用意しています。

もし、その他のLinuxシステム(例えばArch Linux)やARMデバイス(例えばRaspberry)でZettlrを使いたい場合には、自分でパッケージを作る必要があります。electronアプリの作り方については、web上に簡単なチュートリアルがいくらでもあります。サポートされているプラットフォームについては[supported platforms for electron apps](https://github.com/electron/electron/blob/master/docs/tutorial/support.md)を参照してください。

> コミュニティにより管理されているArch Linux向けパッケージがあります。[公式のAURリポジトリにて利用可能です](https://aur.archlinux.org/packages/zettlr-bin/)。このパッケージは、コミュニティにより管理されており、安定性、安全性、提供されるバージョンについて、我々は何の責任も持たないことにご注意ください。

## Windows (7以降)

ZettlrをWindowsにインストールするには、[download page](https://www.zettlr.com/download)からアプリケーションをダウンロードして、ダブルクリックで開くだけです。すべてのユーザーに対してZettlrをインストールする場合は、`Program Files`ディレクトリにインストールされます。この場合、管理者権限での実行の許可を求めるダイアログが、自動的に表示されます。現在のユーザーのみにインストールする場合は、何の権限も必要ありません。

Zettlrのアンインストールは、ディレクトリに置かれているUninstall.exeを実行するか、オペレーティングシステムの設定画面から行ってください。アプリケーションに関連するすべての情報を削除したい場合は、次のディレクトリの削除も行ってください。`C:\Users\<your-user-name>\AppData\Roaming\Zettlr`

## macOS (10.10以降)

ZettlrをmacOSにインストールするには、最新リリースからdmgファイルをダウンロードし、マウントします。その後、Zettlrのアイコンをアプリケーションディレクトリにドラッグしてください。

Zettlrをアンインストールするには、Zettlr.zppをアプリケーションディレクトリから削除するだけです。アプリケーションに関連するすべての情報を削除したい場合は、次のディレクトリの削除も行ってください。`/Users/<your-user-name>/Library/Application Support/Zettlr`

> [Homebrew](https://formulae.brew.sh/cask/zettlr)を使ってインストールすることもできます: `$ brew cask install zettlr`

## Linux (Debian 8/Ubuntu 12.04/Fedora 21 以降)

Linuxシステム向けにビルドされた`deb`パッケージと`rpm`パッケージがあります。単純にパッケージをシステムにインストールしてください。

アンインストールするには、パッケージを削除する通常の手順に従ってください。(多くの場合、グラフィカルなインストーラアプリケーションを使用するか、`dpkg`を使用します。)アプリケーションに関連するすべての情報を削除したい場合は、次のディレクトリの削除も行ってください。`/home/<your-user-name>/.config/Zettlr`

## アップデート

アプリケーションを起動するたびに、新しいアップデートがないかの確認が行われます。また、ヘルプメニュー内の項目から、手動でアップデートの確認を行うこともできます。新しいバージョンが利用可能な場合はダイアログが表示され、新バージョン番号、現在のバージョン番号、新バージョンに含まれる機能とバグ修正が確認できます。そこから、ダウンロードページを開いて新バージョンをダウンロードすることができます。現在のバージョンに上書きでインストールを行うと、まず、旧バージョンの削除を行ってくれます。すべてのデータは保持されたまま、新バージョンに移行されます。

> もし、最先端のリリースに興味があるのなら、設定ダイアログの高度な設定タブにある「ベータ版のリリースを通知する」にチェックを入れてください。

## Pandocのインストール

Zettlrを他のソフトウェア、例えばMicrosoft Word、Wikiシステム、OpenOfficeと連携させるは、`Pandoc`という追加のソフトウェアパッケージを使用します。`Pandoc`はフリーでオープンソースであり、Zettlrのすべてのエクスポート/インポート機能を有効にしてくれます。それにより、Markdownを使っていない協力者とのやり取りが可能になります。

どのプラットフォームでもPandocのインストールは簡単です。

> Pandocはいつでもインストールできます。ヘルプメニュー内の項目からインストールの説明を開くことができます。

### Windows

Windowsの場合、[ダウンロードページ](https://github.com/jgm/pandoc/releases/latest)からWindows用インストーラーをダウンロードし、実行します。それだけで、正常にインストールされるはずです。何かをエクスポートしてみて動作するなら、それで完了です。

> PandocはCLIプログラム(コマンドラインインターフェース)のため、アップデートが利用可能かどうか通知することができません。時々、ダウンロードページを開いて、自分でアップデートの有無を確認してください。

### macOS

macOSの場合、様々な方法でPandocをインストールできます。

#### おすすめの方法: Homebrew

おすすめの方法は、[Homebrew](https://brew.sh/)です。HomebrewはPandocのようなコマンドラインプログラムを簡単にインストールし、メンテナンスするためのパッケージマネージャです。[Homebrewをインストール](https://brew.sh/)してあることを確認し、ターミナルで次のコマンドを実行してください:

```bash
$ brew install pandoc
```

Pandocをアップデートために、時々次のコマンドを実行してください:

```bash
$ brew upgrade
```

これで、すべてのインストール済みformulaが最新バージョンに更新されます。

> 早くて便利なので、Homebrewでのインストールを推奨します。

Pandocのセットアップが終わったら、`citeproc`もインストールしたくなるかもしれません。`citeproc`は、Zettlrの[参考文献](academic/citations.md)機能を利用するために必要です。Windowsでは、Citeprocは自動的にインストールされます。macOSの場合は、Pandoc Citeprocを追加でインストールします。Homebrewで次のコマンドを実行してください:

```bash
$ brew install pandoc-citeproc
```

#### 公式インストーラーを使ったインストール

Pandocをインストールする従来からの方法は、[ダウンロードページ](https://github.com/jgm/pandoc/releases/latest)に行って、macOS用のインストーラをダウンロードし実行することです。完了すれば、Pandocが使えるようになっているはずです。何かをエクスポートしてみて動作するなら、それで完了です。

### Linux

Linuxでのインストールは笑えるほど簡単です。パッケージマネージャでPandocを検索してインストールするだけです。提供されるパッケージは、常に最新とは限りませんが、適切なバージョンのものです。最新バージョンを使用したい場合は、[Linux用インストーラー](https://github.com/jgm/pandoc/releases/latest)を使用して、Pandocのサイトの[インストール手順](https://pandoc.org/installing.html)に従ってください。

> `pandoc-citeproc`の手動インストールが必要な場合があります。お使いのオペレーティングシステムで適切な方法でインストールを行ってください。

## LaTeXのインストール

Markdownは、`LaTeX`と組み合わせることで、美しいPDFファイルを生成することができます。そのためには、Zettlrとともに、`TeX`ディストリビューションをインストールする必要があります。`LaTeX`自体については何も知らなくても使うことができますのでご心配なく。必要なのは、インストールすることだけです。

インストールは、他のソフトウェアと全く同じように行います。WindowsおよびmacOSでは、インストーラパッケージを使用します。Linuxではパッケージマネージャを使用してインストールを行います。

おすすめのディストリビューション:

- Windows: [MikTeX](https://miktex.org/download)
- macOS: [MacTex](https://www.tug.org/mactex/morepackages.html) (_注意: フルバージョンよりはるかに小さいBasic Texをインストールするだけで十分です。_)
- Linux: [TeX Live](https://www.tug.org/texlive/) (texlive-baseパッケージをインストールします。: `sudo apt install texlive-base`)

> LaTeXは、後からインストールすることもできます。ヘルプメニュー内の項目から概要ページを開くと、利用可能なディストリビューションの一覧を確認することができます。
