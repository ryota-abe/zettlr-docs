# Zettelkastenメソッド

The idea to write Zettlr came to my mind several years ago, when we were trying to elaborate on good workflows for academic writing. We tested a lot of different styles and workflow ideas, and one that stuck was the Zettelkasten method. The problem back then was that most of the software did not really succeed in implementing it, but since there has been a lot of effort put into integrating the method, so that nowadays there are more and more applications that support some functions of this method.
Zettlrを作るアイデアが浮かんだのは、数年前にアカデミックな文書を書くワークフローを改善しようとしていた時のことです。様々なスタイルやワークフローのアイデアをテストし、その中から選ばれたのがZettelkastenメソッドでした。その当時は、Zettelkastenをうまく実装したソフトウェアはほとんどありませんでしたが、それから多くの実装の努力が続けられ、現在ではZettelkastenの機能をサポートするアプリケーションが増えてきています。

Originally, the method stems from the German sociologist Niklas Luhmann, who, in an effort to remember everything he's ever read or thought, designed his own (back then analogue) Zettelkasten containing cards with some information and numbers on them. The numbers could be used to locate other cards with other information that was in some way related to the content of the card. This was a way for Luhmann to reference back and forth between a set of cards and, as the box filled up with more and more cards, allowed it to somehow get "alive", showing him connections between certain concepts that he himself had not thought about.
もともと、このメソッドはドイツの社会学者ニクラス・ルーマン(Niklas Luhmann)によって生み出されました。彼は、自分が読んだり考えたことをすべて思い出せるように、情報と番号を書いたカードを使った(当時はアナログでした)Zettelkastenをデザインしました。番号は、カードの情報に関連した情報が書かれた他のカードを探すために使えました。ルーマンはこの方法でカード間の参照を行ったり来たりしました。そして、箱がカードでいっぱいになってくると、これが何らかの形で活きて、自分で考えもしなかったような思考のつながりが見えてきました。

The basic idea, therefore, is to let you create relationships between small notes (or, for that matter, also long files) that enable you not only to move back and forth between files, but also to identify relationships that emerge in your files.
つまり、小さなメモどうしに（または長いファイルでも構いませんが）関連付けを行うことで、ファイル間を行ったり来たりするだけでなく、ファイル間に浮かび上がる関連性を明らかにするというのが、基本的なアイデアです。

## ZettlrでZettelkastenを管理する

Three functions are currently available in Zettlr to kickstart your Zettelkasten:
Zettelkastenを始めるために、Zettlrでは今のところ次の3つの機能が利用できます。

1. ファイルのIDを生成する
2. 検索とファイルへのリンクを作る
3. ファイルにタグを付ける

### ファイルID

One of the biggest problems in writing apps that try to leave files untouched with app-specific stuff is that you need a way to identify files. Internally, Zettlr uses 32Bit-Hashes to identify specific files. But these depend on the paths, and, as Zettlr is designed to work even with cloud-saved files, the path on one computer will not be the same as on another computer, making the hash unusable as an ID. The second difficulty is offered by the format itself: Markdown files are plain text and therefore don't allow for all too much metadata to be added. Of course there have been approaches to integrate headers into markdown files, but this really was not the way to go, because this would jeopardise the rule of Zettlr to write agnostic markdown files. Metadata is way less standardised than the Markdown syntax itself, making it hard to imagine how that could work together with the philosophy of Zettlr. The solution we came up with is to simply bury IDs somewhere in the text. To add an ID to a file, simply press `Cmd/Ctrl+L` to generate one, or, if you prefer to do it manually, simply type an ID yourself. The ID will automatically be highlighted for you.
ファイルにアプリケーション固有のものを残さないようなアプリケーションを作ろうとすると、個々のファイルの識別方法が大きな問題になります。Zettlrは、内部的にファイルを区別するために32bitのハッシュ値を使っています。しかしこれはファイルのパスに依存した値です。Zettlrはクラウドに保存されたファイルも扱えるようにデザインされていて、別のコンピュータ上ではパスが同一とは限らないことから、このハッシュ値をIDとして使うことはできません。もう一つの問題は、フォーマット自体にあります。Markdownファイルはプレーンテキストであるため、余分なメタデータを加えることができません。もちろん、Markdownファイルにヘッダーを追加するというアプローチもあるのですが、その方法はとれませんでした。なぜなら、アプリケーションに依存しないMarkdownファイルを作るというZettlrの原則を破ってしまうからです。Markdowの文法に比べると、メタデータはあまり標準化されていないので、これをZettlrの哲学と両立させる方法は簡単には思いつきません。そこで、私たちは単にIDを文章中に埋め込むことにしました。ファイルにIDを追加するには`Cmd/Ctrl+L`を押してIDを生成します。もしくは、手動でIDを入力すれば、自動的にIDがハイライトされます。

> Take a look at the [Settings page](../reference/settings.md) to see options on how to customise all Zettelkasten functionality to your liking.
> [設定のページ](../reference/settings.md)で、リンクに対するZettelkastenの設定項目をご確認ください。

The default ID is a good call, because it uses the date in the format YYYYMMDDHHMMSS, which is unique to the second. Also, our own experiences show that when one doesn't use easy-to-recognise IDs, one is less prone to assume stuff, making them better suited to cross-link files. Just try it yourself!
デフォルトのIDは良い選択肢です。なぜならYYYYMMDDHHMMSSの日時を使っているので、毎秒ごとに一意な値になるからです。また、経験的に言えることですが、簡単に認識できないIDの方がファイルを相互にリンクするのに向いています。自分で試してみてください。

Zettlr will automatically try to find an ID for a file by searching through its contents. If it has found an ID that is _not_ encapsulated by a Wiki-Link (more on that below), it will assume this ID internally to refer to the file. If there is more than one valid ID in the file, **the first ID will take prevalence**. This way, even in long files, if you can't find the ID, simply drop a new ID on top of the file to make this assume the role of a general ID for the file.
Zettlrは自動的にファイルの内容を検索してIDを自動的に見つけます。発見したIDがWikiリンク形式(詳細は後述)で囲まれていない場合、それをファイルのIDとみなします。

### 内部リンク

Once the problem of Identification was solved, another occurred: How to link files across the app without jeopardising the above-mentioned aims of Zettlr to make files application-independent? Many apps, such as nvALT or The Archive implement an internal linking system that makes it possible to reference files from each other to make navigation through the system as easy as possible. Zettlr also includes such a system.
IDの問題が解決すると次の問題が発生します。前述のように、ファイルをアプリケーションに依存させないというZettlrの目標を達成しつつ、どうすればファイル間にリンクを張ることができるでしょうか。nvALTやThe Archiveのような多くのアプリケーションでは、ファイルの相互参照によりシステム内をできる限り簡単にナビゲートできるような、内部リンクシステムを実装しています。Zettlrも同様に、そのようなシステムを持っています。

An internal link is written with the syntax of `[[This is the link]]`. If you `Alt`- or `Ctrl`-click a link, it will trigger **two** distinct functions. First, it will try to find an exact match of the link's contents in the app. This means that it tries to find a file that reports that the content perfectly matches it. Such an exact match can be found in two ways: First, if the contents of the link (in the above example "This is the link") **exactly** matches a filename, excluding its extension, the appropriate file will report that it is indeed an exact match. The above example would exactly match the files `This is the link.md`, `This is the link.markdown` and `This is the link.txt`. Note that the filename matching is done **case-insensitive**. macOS for instance is by default case insensitive (so `filename.md` would match the same file as `FILENAME.MD`). The second way that such a link may yield an exact match would be if the link's contents contain an ID in the format `[[<your-id>]]`. If any file has the ID `<your-id>`, Zettlr will also yield an exact match. **If an exact match is found somewhere in the system, an Alt-Click on an internal link will immediately open the first matched file**. This means that you can use such links to navigate through your system. You could, for example, accommodate this by creating index files that contain internal links to several files, and in each file, place a link that back-links to the respective index file.
内部リンクは`[[This is the link]]`のような書式で書かれます。`Alt`もしくは`Ctrl`を押しながらリンクをクリックすると、**2つの**異なる機能が実行されます。一つ目は、アプリケーション中でリンクの内容に完全一致するものを探します。つまりリンクに完全一致するような内容を持ったファイルを検索します。この完全一致には2つのパターンがあります。1つはリンクの内容（上の例だと「This is the link」）がファイル名の拡張子を除く部分に完全に一致する場合です。上の例の場合、`This is the link.md`、`This is the link.markdown`、`This is the link.txt`などが完全一致と判定されます。ファイル名の比較は大文字小文字が無視されることにご注意ください。例えばmacOSなどではデフォルトで大文字小文字が無視されます。（なので`filename.md`と`FILENAME.MD`は同一のファイルを示します。）

The second function triggered by such a link is a global search inside your currently selected directory. It will merely take the link contents, place it in your search field and automatically "press Enter", to initiate the search. This way you can not only open exact files, but also find all other files that link to the file you just opened. So a link in the format `[[<your-id>]]` would open that specific file and also search for all files that link back to this file.

### タグ付け

Tagging may be the easiest form of internal searching. If you `Alt`- or `Ctrl`-Click on a tag, this will simply render a search for all files in your current directory that are tagged with this tag. As tags in the form `#keyword` are not used anywhere in the markdown syntax, using this approach enables Zettlr to use such tags as the perfect means to create a tagging system.
